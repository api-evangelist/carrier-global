# Carrier Global (carrier-global)

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
