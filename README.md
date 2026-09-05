# Carrier Global (carrier-global)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Carrier Global Corporation is a global provider of healthy, safe, sustainable, and intelligent building and cold-chain solutions, spanning HVAC, refrigeration, fire, security, and building automation technologies. Its digital ecosystem includes the Lynx Fleet telematics platform (Lynx APIs for transport refrigeration units and marine containers), the Abound building management platform, i-Vu and Carrier Comfort Network for commercial building automation, and the Carrier SmartHome app for residential smart thermostats. Lynx Fleet is the only Carrier product publishing machine-readable API contracts: three OpenAPI 3.0.0 documents covering 16 operations across truck/trailer telematics, two-way refrigeration control and container telemetry, served through the developer portal's public GraphQL backend rather than as static files.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/carrier-global/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Producing
- **Access:** Partner

## Tags

 - HVAC, Cold Chain, Telematics, Building Automation, IoT, Refrigeration, Fortune 500

## Timestamps

- **Created:** 2026-03-21
- **Modified:** 2026-09-05

## APIs

### Carrier Lynx Fleet API

REST API surface exposing Lynx Fleet telematics data for diesel and electric transport refrigeration units (TRUs). Ten operations covering asset inventory, latest-state snapshots, asset and multi-asset history, battery state and battery history, the alarm-code dictionary, and two ingestion endpoints for third-party sensor (SCB) and Orbcomm telematics payloads. Cursor paginated with limit and nextToken, authenticated with a tenant API key in the x-lynx-api-key header.

**Human URL:** [https://doc-api.fleet.lynx.carrier.io/](https://doc-api.fleet.lynx.carrier.io/)

**Base URL:** `https://api.fleet.lynx.carrier.io`

#### Tags

 - Cold Chain, Telematics, Fleet, Refrigeration, IoT

#### Properties

- [OpenAPI](openapi/carrier-global-lynx-fleet-api-openapi.yaml)
- [Overlay](overlays/carrier-global-lynx-fleet-api-overlay.yaml)
- [Documentation](https://doc-api.fleet.lynx.carrier.io/)
- [API Reference](https://api.tta.lynxfleet.carrier.com/apis)
- [Portal](https://api.tta.lynxfleet.carrier.com/)
- [Getting Started](https://doc-api.fleet.lynx.carrier.io/api-documentation)
- [Terms of Service](https://www.carrier.com/lynx/terms-of-use)
- [Products](https://api.tta.lynxfleet.carrier.com/products)

### Carrier Lynx 2-way Command API

Remote-control surface for Lynx-connected transport refrigeration units. Three operations: list the commands a given asset supports, send one or more commands, and check the status of a dispatched command by commandId. Commands include per-compartment setpoints in the range -30 to 35 °C, compartment toggles, defrost initiation, pre-trip initiation, alarm clearing, run mode, sleep mode, TRU power and Intelliset selection. This is physical actuation: Carrier publishes no idempotency key, no dry-run mode and no reversal operation for it.

**Human URL:** [https://doc-api.fleet.lynx.carrier.io/](https://doc-api.fleet.lynx.carrier.io/)

**Base URL:** `https://api.fleet.lynx.carrier.io/2waycmd`

#### Tags

 - Cold Chain, Refrigeration, Remote Control, Telematics, IoT

#### Properties

- [OpenAPI](openapi/carrier-global-lynx-2way-command-api-openapi.yaml)
- [Overlay](overlays/carrier-global-lynx-2way-command-api-overlay.yaml)
- [Documentation](https://doc-api.fleet.lynx.carrier.io/)
- [API Reference](https://api.tta.lynxfleet.carrier.com/apis)

### Carrier Lynx Container API

Telemetry surface for Carrier-managed marine and intermodal refrigerated containers, published as a separate contract with its own data model. Three operations: the container Unified Model property and alarm definitions, latest source data, and container asset history. Shares the x-lynx-api-key authentication, the error envelope and the monthly call quota with the fleet API, but shares none of its schemas.

**Human URL:** [https://doc-api.fleet.lynx.carrier.io/](https://doc-api.fleet.lynx.carrier.io/)

**Base URL:** `https://api.fleet.lynx.carrier.io/coa`

#### Tags

 - Cold Chain, Container, Telematics, Refrigeration, IoT

#### Properties

- [OpenAPI](openapi/carrier-global-lynx-container-api-openapi.yaml)
- [Overlay](overlays/carrier-global-lynx-container-api-overlay.yaml)
- [Documentation](https://doc-api.fleet.lynx.carrier.io/)
- [API Reference](https://api.tta.lynxfleet.carrier.com/apis)

### Carrier Lynx Dev Portal GraphQL

The GraphQL backend behind the Lynx Fleet Dev Portal. Its /public/graphql endpoint answers anonymously and is the only way to reach Carrier's API contracts and integration guides in machine-readable form — the docs host is a single-page app that returns an HTML shell for every conventional spec path. Verified queries: getDefaultProducts (the product catalogue), getPublicApiSpecYml and getPublicApiSpecJson (the OpenAPI documents), and getPublicProductInfo (contract plus structured guide). Introspection is disabled.

**Human URL:** [https://doc-api.fleet.lynx.carrier.io/](https://doc-api.fleet.lynx.carrier.io/)

**Base URL:** `https://api.portal.fleet.lynx.carrier.io/public/graphql`

#### Tags

 - GraphQL, Developer Portal, Discovery

#### Properties

- [GraphQL](graphql/carrier-global-lynx-portal-graphql.yml)
- [Documentation](https://doc-api.fleet.lynx.carrier.io/)

### Carrier i-Vu Building Automation

i-Vu is Carrier's web-based commercial building automation system for monitoring and controlling HVAC, lighting, and related building systems. It integrates with BACnet and other standard building protocols rather than a public REST API surface.

**Human URL:** [https://www.carrier.com/commercial/en/us/products/controls/building-automation/](https://www.carrier.com/commercial/en/us/products/controls/building-automation/)

#### Tags

 - Building Automation, BACnet, HVAC

#### Properties

- [Documentation](https://www.carrier.com/commercial/en/us/products/controls/building-automation/)

### Carrier Comfort Network

Carrier Comfort Network (CCN) is Carrier's proprietary control and communication network for tying together chillers, air handlers, and related HVAC equipment, typically integrated into BMS/BAS deployments.

**Human URL:** [https://www.carrier.com/commercial/en/us/products/controls/carrier-comfort-network/](https://www.carrier.com/commercial/en/us/products/controls/carrier-comfort-network/)

#### Tags

 - Building Automation, HVAC, Chillers

#### Properties

- [Documentation](https://www.carrier.com/commercial/en/us/products/controls/carrier-comfort-network/)

### Carrier Abound

Abound is Carrier's cloud-based building intelligence platform that aggregates data from HVAC, IAQ sensors, and occupancy systems to provide indoor-environmental-quality analytics, energy insights, and healthy-building dashboards for commercial real estate operators.

**Human URL:** [https://abound.carrier.com](https://abound.carrier.com)

#### Tags

 - Building Intelligence, IAQ, Analytics

#### Properties

- [Documentation](https://abound.carrier.com)

### Carrier SmartHome App

The Carrier SmartHome app lets homeowners remotely control Carrier connected smart thermostats and residential HVAC equipment. No public developer API is currently published; integration is via the consumer mobile app and connected thermostat web portals.

**Human URL:** [https://www.carrier.com/residential/en/us/products/thermostats/](https://www.carrier.com/residential/en/us/products/thermostats/)

#### Tags

 - Smart Home, Thermostats, Residential

#### Properties

- [Documentation](https://www.carrier.com/residential/en/us/products/thermostats/)

## Use Cases

- Cold-chain compliance and pharmaceutical or food logistics where carriers pull real-time TRU temperature, door events, alarms and GPS into an existing TMS through the Lynx Fleet API.
- Two-way fleet command and control where dispatchers remotely change a setpoint, initiate defrost or pre-trip, or power a refrigeration unit in response to a route or load change.
- Marine and intermodal container telemetry through the separate Lynx Container API, including Pre-Trip Inspection and TripWise data.
- Battery health monitoring across a trailer fleet, using the asset-battery and battery-history operations.
- Alarm triage, resolving codes seen on assets against the published alarm-code dictionary.
- Indoor environmental quality analytics and healthy-building scoring for commercial real estate operators using Abound building telemetry (no public contract).
- Commercial HVAC scheduling, trending and alarm routing through i-Vu for multi-site building operators (BACnet integration, no public REST contract).

## Common Properties

- [Website](https://www.corporate.carrier.com)
- [Consumer Site](https://www.carrier.com/us/en/)
- [LinkedIn](https://www.linkedin.com/company/carrier)
- [Lynx Fleet Dev Portal](https://doc-api.fleet.lynx.carrier.io/)
- [Lynx Fleet Developer Portal](https://api.tta.lynxfleet.carrier.com/)
- [API Reference](https://api.tta.lynxfleet.carrier.com/apis)
- [Getting Started](https://doc-api.fleet.lynx.carrier.io/api-documentation)
- [Lynx Fleet Developer Portal sign in](https://api.tta.lynxfleet.carrier.com/signin)
- [Support](https://www.corporate.carrier.com/contact-us/)
- [Carrier News](https://www.corporate.carrier.com/news/)
- [Terms of Service](https://www.corporate.carrier.com/legal/terms-of-use/)
- [Privacy Policy](https://www.corporate.carrier.com/legal/privacy-notice/)
- [Carrier PSIRT — report a vulnerability](https://www.carrier.com/us/en/product-security/report-an-issue.html)
- [Carrier Product and Software Security Assurance](https://www.carrier.com/us/en/product-security.html)
- [Authentication](authentication/carrier-global-authentication.yml)
- [Conventions](conventions/carrier-global-conventions.yml)
- [Error Catalog](errors/carrier-global-problem-types.yml)
- [Lifecycle](lifecycle/carrier-global-lifecycle.yml)
- [Conformance](conformance/carrier-global-conformance.yml)
- [Data Model](data-model/carrier-global-data-model.yml)
- [Rate Limits](rate-limits/carrier-global-rate-limits.yml)
- [Plans](plans/carrier-global-plans-pricing.yml)
- [FinOps](finops/carrier-global-finops.yml)
- [Vocabulary](vocabulary.yml)
- [Lynx Fleet Dev Portal interactive API console](sandbox/carrier-global-sandbox.yml)
- [Lynx Push API (documented webhook surface)](asyncapi/carrier-global-lynx-webhooks.yml)
- [Packages](packages/carrier-global-packages.yml)
- [Agent Skills](skills/_index.yml)
- [Tool Crosswalk](mcp/carrier-global-tool-crosswalk.yml)
- [MCP Server (candidate — no server exists)](mcp/carrier-global-mcp.yml)
- [Well-Known Probe](well-known/carrier-global-well-known.yml)
- [Domain Security](security/carrier-global-domain-security.yml)
- [Vulnerability Disclosure](security/carrier-global-vulnerability-disclosure.yml)
- [llms.txt](llms/carrier-global-llms.txt)
- [Investor Relations](https://ir.carrier.com)
- [Careers](https://www.corporate.carrier.com/careers/)
- [Contact](https://www.corporate.carrier.com/contact-us/)
- [JSON-LD Context](json-ld/carrier-global-context.jsonld)
- [Spectral Rules](spectral/carrier-global.spectral.yml)

## Maintainers

**FN:** Kin Lane

**Email:** info@apievangelist.com
