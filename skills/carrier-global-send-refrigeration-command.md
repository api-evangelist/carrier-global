---
name: carrier-global-send-refrigeration-command
description: >-
  Send a two-way command to a Carrier LYNX transport refrigeration unit — change a
  setpoint, initiate defrost or pre-trip, clear alarms, or power the unit — and confirm
  the outcome. THIS ACTUATES PHYSICAL EQUIPMENT ON A REAL VEHICLE.
api: carrier-global:lynx-2way-command-api
server: https://api.fleet.lynx.carrier.io/2waycmd
operations:
  - get-2way-commands
  - send-2way-commands
  - check-2way-command-status
generated: '2026-09-05'
method: generated
source: openapi/carrier-global-lynx-2way-command-api-openapi.yaml
---

# Send a LYNX two-way refrigeration command

**Read this section before anything else.** This is the only write surface Carrier
publishes with real-world consequence, and the contract gives you none of the usual
safety rails:

- **No idempotency key.** Nothing in the contract or the guide deduplicates a retried
  command. A network timeout followed by a retry can double-fire.
- **No dry-run and no sandbox.** Carrier publishes no test host, no test key and no
  fixture assets. The first call you make is a real one.
- **No cancel, no undo, no reversal window.** `check-command-status` observes; it does
  not reverse. A setpoint can be re-set by sending another command, but a
  `DefrostInitiation`, `InitiatePretrip`, `ClearAlarms` or `TRUOnOff` cannot be taken
  back.
- **Carrier's own precondition:** "These commands should be executed only if TRU
  (cooling unit) is powered on."

Treat `send-2way-commands` as human-confirmed. Do not auto-invoke it from an
unsupervised loop.

## 1. Ask what the asset supports — `get-2way-commands`

    GET https://api.fleet.lynx.carrier.io/2waycmd/v1/get-commands?assetId=<uuid>
    x-lynx-api-key: <key>

One of `assetId`, `assetName` or `truSerialNumber` is required. The response is a
capability map — a boolean per command name — so never assume support. Commands that
appear in the model: `CompartmentSetpoint1`, `CompartmentSetpoint2`,
`CompartmentSetpoint3`, `ToggleCompartment1/2/3`, `RunMode`, `DefrostInitiation`,
`ClearAlarms`, `InitiatePretrip`, `TRUOnOff`, `SleepMode`, `GetActiveIntellisetId`,
`SetActiveIntelliset`.

## 2. Send it — `send-2way-commands`

    POST https://api.fleet.lynx.carrier.io/2waycmd/v1/send-commands
    x-lynx-api-key: <key>
    Content-Type: application/json

`Send2wayCmdRequestBody` requires `assetId` and carries one or more command properties
alongside it. Setpoints are numbers in the documented range **[-30, 35] °C** (equivalently
[-22, 95] °F) per compartment. `SetActiveIntelliset` takes
`{"compartmentNumber": 1–3, "activeIntelliset": 1–31}`.

The response is `Send2wayResponse`, an array of `SentCommand`, each carrying a
`commandId` (UUID). **Persist that `commandId` before doing anything else** — it is your
only handle on the command, and losing it means you cannot confirm the outcome.

Prefer absolute-value commands over toggles where you have the choice. Setting
`CompartmentSetpoint1: -18` twice lands in the same place; `ToggleCompartment1` twice
does not.

## 3. Confirm — `check-2way-command-status`

    GET https://api.fleet.lynx.carrier.io/2waycmd/v1/check-command-status?commandId=<uuid>&assetId=<uuid>
    x-lynx-api-key: <key>

Returns `CommandsStatusList` — `CommandsStatus` records carrying `commandId`, `assetId`,
`deviceId` and `tenantId` alongside the status. Poll this rather than assuming the
command landed; delivery to a vehicle is asynchronous and depends on the unit being
reachable.

## Failure handling

`{"message": "..."}` with 400/401/403/429/500, same as the rest of LYNX.

On a **timeout with no response body**, do not blind-retry a command. Call
`check-2way-command-status` for the asset first and look for a command you may already
have created; only re-send if nothing is there. This is the manual substitute for the
idempotency key Carrier does not provide.
