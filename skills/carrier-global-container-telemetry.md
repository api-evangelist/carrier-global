---
name: carrier-global-container-telemetry
description: >-
  Read Carrier LYNX container (marine reefer) telemetry — the Unified Model definitions,
  latest source data, and container asset history. Read-only. A separate data model from
  the truck/trailer API.
api: carrier-global:lynx-container-api
server: https://api.fleet.lynx.carrier.io/coa
operations:
  - unified-model-v1
  - container-snapshot-v1
  - container-asset-history-list-v1
generated: '2026-09-05'
method: generated
source: openapi/carrier-global-lynx-container-api-openapi.yaml
---

# Read LYNX container telemetry

Read-only.

## The thing to know first

The container API is **not** the truck/trailer API with a different base path. It shares
the authentication scheme, the error envelope and the status codes, and it shares
nothing else: it is `SourceData` and `UnifiedModel`, keyed on `SourceId` and `DeviceId`,
where the fleet API is `Asset`, keyed on `assetId`. None of the `Asset`, `AssetSnapshot`,
`StatusInfo` or `TemperatureInfo` schemas appears here.

If you are covering both truck/trailer and container fleets, you are writing two
mappings. Plan for that.

## 1. Learn the vocabulary — `unified-model-v1`

    GET https://api.fleet.lynx.carrier.io/coa/v1/api/core2/UnifiedModel
    x-lynx-api-key: <key>

Returns `UnifiedModelList` — the `UnifiedModelProperty` and `UnifiedModelAlarm`
definitions. Fetch and cache this before reading data; the telemetry records reference
it, and without it the property and alarm identifiers are opaque.

## 2. Latest state — `container-snapshot-v1`

    GET https://api.fleet.lynx.carrier.io/coa/v1/api/core2/sourcelatestdata
    x-lynx-api-key: <key>

Returns `SourceDataList` — `SourceData` records carrying `SourceId` and `DeviceId`.

## 3. History — `container-asset-history-list-v1`

    GET https://api.fleet.lynx.carrier.io/coa/v1/api/core2/container-asset-history-items
    x-lynx-api-key: <key>

Returns `SourceDataHistoryList`.

## Shared rules

Same key header, same HTTPS/TLS 1.2 requirement, same `{"message": "..."}` errors on
400/401/403/429/500, and the same 500,000-calls-per-month budget — the quota is per key
across all three LYNX contracts, not per contract.

Carrier's container guide adds Pre-Trip Inspection and TripWise data to the described
offering alongside GPS, sensor readings, key events and alarms, and asset status.
