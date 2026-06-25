# Wi-Fi Adapter Not Detected

- **Category:** Networking
- **OSI Layer:** 1-2 (Physical / Data Link)
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- No Wi-Fi networks listed
- Adapter missing from Device Manager / `ip link`
- Airplane mode toggle has no effect

## Environment
- OS, and whether this started right after an update

## Diagnostic Steps
1. Check Device Manager (incl. hidden devices) or `lspci` / `ip link` (Linux).
2. Confirm the physical Wi-Fi kill switch/airplane mode is actually off.
3. Check whether the adapter shows in BIOS — confirms hardware vs. driver fault.
4. Try reinstalling the manufacturer's Wi-Fi driver.

## Root Cause
Usually a driver corrupted by an update; less commonly the M.2 Wi-Fi card has come loose internally, especially after a RAM/drive upgrade.

## Solution
1. If missing from Device Manager entirely: uninstall it and "Scan for hardware changes."
2. Reinstall the manufacturer's Wi-Fi driver — not the generic Windows one.
3. If it shows in BIOS but not the OS: clean-install the driver in Safe Mode.
4. If not visible in BIOS either: physically reseat the M.2 Wi-Fi card (requires opening the chassis).

## Verification
- Adapter appears in Device Manager/`ip link` and connects to a known network.

## Prevention
- Set Windows Update to "notify only" for network adapter drivers.

## Tags
`laptop` `wifi` `network` `driver`
