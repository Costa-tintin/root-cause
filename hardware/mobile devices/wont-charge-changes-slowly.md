# Won't Charge / Charges Slowly

- **Category:** Hardware
- **OSI Layer:** N/A
- **Date documented:** 2026-05-25
- **Status:** Resolved

## Symptoms
- Plugged in but battery % doesn't rise, or rises very slowly
- Charging icon flickers on/off
- Phone warm near the port while "charging"

## Environment
- Charger/cable used (OEM vs third-party)
- Port type (USB-C/Lightning), OS version

## Diagnostic Steps
1. Test with a different known-good cable and charger to isolate cable vs port vs battery.
2. Inspect the charging port for lint/debris with a flashlight.
3. Check the battery health setting for degraded capacity.
4. Check Settings > Battery for an app holding a wake lock that draws more than the charger supplies.

## Root Cause
Most often debris in the port blocking contact, or a worn cable; less commonly a degraded battery or a backgrounded app outdrawing the charger.

## Solution
1. Clean the port gently with a wooden toothpick or compressed air — never metal.
2. Swap to an OEM cable/charger to rule out a damaged third-party one.
3. If still slow with a clean port and good cable: confirm the charger's wattage matches the phone's fast-charge spec.
4. If battery health is below ~80%: this is hardware wear — replacement is the fix.

## Verification
- Charging resumes at the expected rate (check % gain over 15 minutes).

## Prevention
- Use OEM-rated cables/chargers.
- Clean the port periodically.

## Tags
`mobile` `hardware` `battery` `charging`
