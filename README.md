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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Carrier Global Corporation is a global provider of healthy, safe, sustainable, and intelligent building and cold-chain solutions, spanning HVAC, refrigeration, fire, security, and building automation technologies. Its digital ecosystem includes the Lynx Fleet telematics platform (Lynx APIs for transport refrigeration units), the Abound building management platform, i-Vu and Carrier Comfort Network for commercial building automation, and the Carrier SmartHome app for residential smart thermostats.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/carrier-global/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Provider
- **Access:** Partner

## Tags

 - HVAC, Cold Chain, Telematics, Building Automation, IoT, Refrigeration, Fortune 500

## Timestamps

- **Created:** 2026-03-21
- **Modified:** 2026-04-23

## APIs

### Carrier Lynx Fleet API

REST API surface exposing Lynx Fleet telematics and control data for diesel and electric transport refrigeration units (TRUs). Enables systems integrators to pull asset inventory, setpoints, temperatures, alarms, and GPS location, and to issue two-way commands to connected refrigeration units directly from existing transport-management systems.

**Human URL:** [https://doc-api.fleet.lynx.carrier.io/](https://doc-api.fleet.lynx.carrier.io/)

#### Tags

 - Cold Chain, Telematics, Fleet, Refrigeration, IoT

#### Properties

- [Documentation](https://doc-api.fleet.lynx.carrier.io/api-documentation)
- [Portal](https://api.tta.lynxfleet.carrier.com/)
- [Reference](https://doc-api.fleet.lynx.carrier.io/docs/lynx-prod-api/1/routes/v1/assets/get)
- [Products](https://api.tta.lynxfleet.carrier.com/products)

### Carrier i-Vu Building Automation

i-Vu is Carrier's web-based commercial building automation system for monitoring and controlling HVAC, lighting, and related building systems. It integrates with BACnet and other standard building protocols rather than a public REST API surface.

**Human URL:** [i-Vu Building Automation](https://www.carrier.com/commercial/en/us/software/building-automation/i-vu-building-automation/)

#### Tags

 - Building Automation, BACnet, HVAC

### Carrier Comfort Network

Carrier Comfort Network (CCN) is Carrier's proprietary control and communication network for tying together chillers, air handlers, and related HVAC equipment, typically integrated into BMS/BAS deployments.

#### Tags

 - Building Automation, HVAC, Chillers

### Carrier Abound

Abound is Carrier's cloud-based building intelligence platform that aggregates data from HVAC, IAQ sensors, and occupancy systems to provide indoor-environmental-quality analytics, energy insights, and healthy-building dashboards for commercial real estate operators.

#### Tags

 - Building Intelligence, IAQ, Analytics

### Carrier SmartHome App

The Carrier SmartHome app lets homeowners remotely control Carrier connected smart thermostats and residential HVAC equipment. No public developer API is currently published; integration is via the consumer mobile app and connected thermostat web portals.

#### Tags

 - Smart Home, Thermostats, Residential

## Use Cases

- Cold-chain compliance and pharmaceutical or food logistics where carriers need to pull real-time TRU temperature, door events, and fuel levels into existing TMS platforms through the Lynx Fleet API.
- Two-way fleet command and control where dispatchers remotely start, stop, or re-setpoint a refrigeration unit in response to a route or load change.
- Geofence-triggered automation for pre-cool, arrival, or departure workflows at distribution centers.
- Indoor environmental quality (IEQ) analytics and healthy-building scoring for commercial real estate operators using Abound building telemetry.
- Commercial HVAC scheduling, trending, and alarm routing through i-Vu for multi-site building operators.
- Residential thermostat control and comfort scheduling through the Carrier SmartHome app.

## Common Properties

- [Website](https://www.corporate.carrier.com)
- [Consumer Site](https://www.carrier.com/us/en/)
- [Lynx Fleet API Documentation](https://doc-api.fleet.lynx.carrier.io/)
- [Lynx Fleet Developer Portal](https://api.tta.lynxfleet.carrier.com/)
- [Getting Started](https://doc-api.fleet.lynx.carrier.io/api-documentation)
- [Abound](https://www.carrier.com/commercial/en/us/software/abound/)
- [Building Automation (i-Vu)](https://www.carrier.com/commercial/en/us/software/building-automation/i-vu-building-automation/)
- [SmartHome](https://www.carrier.com/residential/en/us/smart-thermostats/smarthome-app/)
- [Investor Relations](https://ir.carrier.com)
- [Careers](https://careers.corporate.carrier.com)
- [Contact](https://www.corporate.carrier.com/contact-us/)
- [JSON-LD Context](json-ld/carrier-global-context.jsonld)
- [Vocabulary Definition](vocabulary.yml)
- [Spectral Rules](spectral/carrier-global.spectral.yml)

## Maintainers

**FN:** Kin Lane

**Email:** info@apievangelist.com
