# Won't Boot / Black Screen

- **Category:** Hardware
- **OSI Layer:** N/A
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- Power LED on, fans spin, but screen stays black
- No POST beep, or a beep code pattern plays
- Screen flickers briefly then goes dark

## Environment
- Laptop model, RAM/SSD configuration
- Whether an external monitor has been tested yet

## Diagnostic Steps
1. Connect an external monitor via HDMI to isolate display vs. motherboard fault.
2. Remove the battery (if removable), power via AC only, hold power 30s to clear static charge.
3. Reseat RAM and listen for beep codes.
4. Try entering BIOS (F2/Del) — if BIOS displays, the fault is OS-level, not hardware.

## Root Cause
Most often a loose RAM seat or a failed display backlight/inverter; confirmed by whether the external monitor test shows an image.

## Solution
1. If the external display works: boot into Safe Mode and update/roll back the GPU driver, or repair the bootloader.
2. If reseating RAM produces a clean beep/boot: clean contacts with isopropyl alcohol and reseat firmly.
3. If still black even on the external monitor: the backlight, inverter, or screen cable needs hardware replacement.

## Verification
- Laptop POSTs and reaches desktop on its own screen, without the external monitor.

## Prevention
- Discharge static before reseating RAM.
- Keep BIOS/firmware updated.

## Tags
`laptop` `hardware` `boot` `no-display`
