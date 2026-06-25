# PoE Port Not Powering Device

- **Category:** Hardware
- **OSI Layer:** 1 (Physical)
- **Date documented:** 2026-01-1
- **Status:** Resolved

## Symptoms
- PoE device (AP, phone, camera) has no power/link light despite being plugged in

## Environment
- Switch PoE budget/wattage, device's PoE class (802.3af/at/bt), cable length/quality

## Diagnostic Steps
1. `show power inline` — check the port's PoE status and the switch's total power budget used.
2. Confirm the cable is wired correctly — PoE needs all 4 pairs on gigabit links.
3. Test the device on a different known-good PoE port.
4. Check the device's required PoE class against what the port/switch supports.

## Root Cause
Most often the switch has hit its total PoE power budget, or the device needs a higher PoE class than the port provides.

## Solution
1. If budget exceeded: move lower-priority PoE devices to a different switch, or upgrade the switch's PSU.
2. If class mismatch: move the device to a port/switch supporting the required PoE standard.
3. If cable issue: replace with a verified Cat5e/6 cable wired straight-through.
4. As a check, re-enable the port explicitly: `power inline auto` after `no power inline never`.

## Verification
- Device powers on; `show power inline` shows the port "on" with correct wattage allocated.

## Prevention
- Track total PoE budget before adding new devices.
- Label ports by PoE class supported.

## Tags
`switch` `poe` `hardware` `power`
