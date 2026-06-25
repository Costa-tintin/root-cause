# No Cellular Signal After Update

- **Category:** Networking
- **OSI Layer:** 1-2 (carrier radio layer)
- **Date documented:** 2026-05-25
- **Status:** Resolved

## Symptoms
- "No Service" or SOS-only right after an OS update
- Wi-Fi still works fine

## Environment
- Carrier, OS version before/after update, dual-SIM or eSIM

## Diagnostic Steps
1. Check whether Airplane Mode got toggled on by the update.
2. Toggle Airplane Mode on then off to force a radio re-registration.
3. Check for a pending carrier settings update.
4. Reseat the physical SIM, or confirm the eSIM profile still shows active.

## Root Cause
Most commonly the update reset baseband/radio state or carrier settings didn't auto-apply; rarely a SIM contact issue.

## Solution
1. Toggle Airplane Mode on, wait 10 seconds, toggle off.
2. Install the carrier settings update if prompted.
3. Reset Network Settings if the above doesn't help (this also clears saved Wi-Fi — warn the user first).
4. If SIM-based: remove and reseat the SIM card.

## Verification
- Signal bars return and a test call/data session succeeds.

## Prevention
- Check for a carrier settings update right after any OS update.

## Tags
`mobile` `network` `cellular` `update`
