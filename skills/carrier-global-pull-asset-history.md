---
name: carrier-global-pull-asset-history
description: >-
  Pull temperature, position, alarm and battery history for Carrier LYNX transport
  refrigeration assets, batching correctly and staying inside the published quota.
  Read-only.
api: carrier-global:lynx-fleet-api
server: https://api.fleet.lynx.carrier.io
operations:
  - asset-history-list-v1
  - multi-asset-history-v1
  - asset-battery-list-v1
  - asset-battery-history-list-v1
  - multi-asset-battery-history-v1
generated: '2026-09-05'
method: generated
source: openapi/carrier-global-lynx-fleet-api-openapi.yaml
---

# Pull LYNX asset history

Read-only. Two of these operations use `POST`, but only to carry a list of asset
identifiers in the body — they write nothing.

## Choosing the right operation

| Need | Operation | Constraint |
|---|---|---|
| One asset, a window of events | `asset-history-list-v1` (`GET /v1/asset-history-items`) | 1 asset per request |
| Several assets, same window | `multi-asset-history-v1` (`POST /v1/multi-asset-history`) | 10 assets per request |
| Battery state now | `asset-battery-list-v1` (`GET /v1/asset-batteries`) | paginated |
| Battery events, one asset | `asset-battery-history-list-v1` (`GET /v1/asset-battery-history`) | 1 asset |
| Battery events, several assets | `multi-asset-battery-history-v1` (`POST /v1/multi-asset-battery-history`) | list in body |

Carrier's stated recommendation for all of these is a **30-minute** window. Longer
windows are supported ("get all events within a specified duration (several days)") but
30 minutes is what they tune for.

## Single asset

    GET https://api.fleet.lynx.carrier.io/v1/asset-history-items?assetIds=<id>&limit=250
    x-lynx-api-key: <key>

Returns `AssetHistoryList` — pages of `AssetHistoryEntry`, each composing `AssetInfo`,
`StatusInfo`, `TemperatureInfo`, `PositionInfo`, `AlarmInfo`, `CommandInfo` and
`Sensor`. Page with `nextToken`. Results come back newest first.

## Ten assets at a time

    POST https://api.fleet.lynx.carrier.io/v1/multi-asset-history
    x-lynx-api-key: <key>
    Content-Type: application/json

The `MultiAssetHistoryRequest` body models the four ways of naming assets as four
parallel parameter objects — `AssetParamWithId`, `AssetParamWithName`,
`AssetParamWithTruSerialNumber`, `AssetParamWithLicensePlateNumber`. Pick one shape and
stay with it. The response is a `MultiAssetHistory` array of `MultiAssetHistoryItem`,
each holding `MultiAssetHistoryEntry` records with the same composition as the
single-asset form.

Batching here is the main lever on the monthly quota: ten assets in one call instead of
ten calls.

## Quota arithmetic

500,000 calls per month, per key. A fleet of 500 assets polled every 30 minutes through
`multi-asset-history` at 10 assets per call is 50 calls per cycle, 48 cycles a day —
about 72,000 calls a month. The same fleet polled one asset at a time is 720,000, which
does not fit. Do the arithmetic before you design the loop.

Excess usage may incur additional charges; a higher limit is a conversation with the
Carrier Lynx Integration Team.

## Failure handling

Same envelope as everywhere in LYNX: `{"message": "..."}`, statuses 400/401/403/429/500.
On 429 back off exponentially — there is no `Retry-After` header. Use a 30-second
timeout and retry transient failures with backoff, but note there is **no idempotency
key** on this API; retries on the read paths are safe, retries on write paths are not.
