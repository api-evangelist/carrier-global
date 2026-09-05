---
name: carrier-global-monitor-cold-chain
description: >-
  Monitor a Carrier LYNX transport-refrigeration fleet — inventory the assets a key can
  see, pull their latest snapshots, and resolve any alarm codes into human-readable
  descriptions. Read-only.
api: carrier-global:lynx-fleet-api
server: https://api.fleet.lynx.carrier.io
operations:
  - asset-list-v1
  - asset-snapshot-list-v1
  - alarm-codes-and-descriptions-v1
generated: '2026-09-05'
method: generated
source: openapi/carrier-global-lynx-fleet-api-openapi.yaml
---

# Monitor a Carrier LYNX cold-chain fleet

Read-only. Nothing in this skill changes state on a vehicle.

## Before you start

Every request carries the tenant API key in the `x-lynx-api-key` header, over HTTPS.
The key is entitlement-scoped by Carrier: it sees the tenants, assets and data types
that were configured for it, and nothing else. A `403` means the configuration does not
cover what you asked for — do not retry it, ask the Carrier Lynx Integration Team to
extend the entitlement.

Budget: 500,000 calls per month across the key. There is no header telling you how much
is left, so count your own calls.

## 1. Inventory the fleet — `asset-list-v1`

    GET https://api.fleet.lynx.carrier.io/v1/assets?limit=250
    x-lynx-api-key: <key>

With no filter parameters you get every asset the key is entitled to. Page with
`nextToken` until it stops coming back; `limit` accepts 1–250 and defaults to 100.

Carrier's own guidance: **sync this list once a week and cache it.** Re-listing assets
before every read is the documented way to burn the monthly quota and to trip 400-level
asset-id errors.

Assets can also be addressed by `assetNames`, `truSerialNumbers` or
`licensePlateNumbers` — all comma-separated, all interchangeable with `assetIds`.

## 2. Pull current state — `asset-snapshot-list-v1`

    GET https://api.fleet.lynx.carrier.io/v1/asset-snapshots?assetIds=<id>,<id>&limit=250
    x-lynx-api-key: <key>

Each `AssetSnapshot` composes the asset with its `StatusInfo` (28 operating-state
fields), `TemperatureInfo` (27 setpoint and probe fields), `PositionInfo` (GPS),
`AlarmInfo` (an array of `Alarm`) and `ConnectedTruckInfo` (the tractor currently paired
to a trailer).

This is the right call for an ad-hoc status check. Carrier recommends a **30-minute**
cadence. If you need to know faster than that, you want the Push API (webhooks), not a
tighter poll — see `asyncapi/carrier-global-lynx-webhooks.yml`, and note that its event
catalog is not published, so arranging it goes through Carrier.

## 3. Resolve alarms — `alarm-codes-and-descriptions-v1`

    GET https://api.fleet.lynx.carrier.io/v1/alarm-codes-and-descriptions
    x-lynx-api-key: <key>

Returns the alarm-code dictionary. Fetch it once and cache it; codes on snapshots and
history entries are meaningless without it.

## Handling failures

Errors are `{"message": "..."}` with no machine-readable code, so branch on the HTTP
status:

| Status | Meaning | Do |
|---|---|---|
| 400 | Missing or incorrect parameter | Fix the request. A stale asset-id cache is the common cause. |
| 401 | Invalid or missing API key | Check the header and that you are on HTTPS. |
| 403 | Key lacks permission | Stop. Escalate to Carrier; retrying will not help. |
| 429 | Quota or rate exceeded | Exponential backoff with jitter. No `Retry-After` is sent. |
| 500 | Server error | Retry with backoff; escalate if persistent. |

Use a 30-second call timeout, and decouple retrieval from processing — pull, queue,
then process asynchronously.

Ignore response fields you do not recognise, and tolerate fields that are absent.
Carrier states both as consumer obligations, and adding response properties is
explicitly a non-breaking change under their versioning policy.
