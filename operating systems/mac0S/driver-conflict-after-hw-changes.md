# Driver/Peripheral Conflict After Hardware Change

- **Category:** OS
- **OSI Layer:** N/A
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- A newly connected display, dock, or peripheral causes kernel panics, freezes, or isn't recognized
- Existing peripherals stop working too

## Environment
- macOS version, the specific peripheral/dock added, Apple Silicon vs Intel

## Diagnostic Steps
1. Check System Information > USB/Thunderbolt to see if the device is detected at all.
2. Check Console.app for kernel panic logs around the time of the conflict.
3. Disconnect the new peripheral and confirm the system stabilizes.
4. Check the peripheral manufacturer's site for a macOS compatibility note or required System Extension.

## Root Cause
Usually a third-party System Extension for the new peripheral that hasn't been approved in Privacy & Security, or a genuine compatibility gap with the current macOS version.

## Solution
1. Go to System Settings > Privacy & Security and approve the pending extension if one is blocked there.
2. Update the peripheral's driver/companion software to the latest version for the current macOS release.
3. If no compatible driver exists yet, use the peripheral in a basic mode until support is released.

## Verification
- Peripheral works normally with no further kernel panics over a full day of use.

## Prevention
- Check macOS compatibility before connecting new docks/peripherals, especially after a macOS upgrade.

## Tags
`macos` `driver` `peripheral` `hardware`
