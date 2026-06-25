# Driver Fails After Windows Update

- **Category:** OS
- **OSI Layer:** N/A
- **Date documented:** 2026-05-25
- **Status:** Resolved

## Symptoms
- Printer worked, then after a Windows update shows an error or won't print
- Driver appears "unavailable"

## Environment
- Windows build before/after the update, printer driver version

## Diagnostic Steps
1. Check Device Manager for a warning icon on the printer/print queue driver.
2. Compare the Windows Update history date against when the issue started.
3. Try the Microsoft IPP Class Driver as an alternate driver mode if available.
4. Check the manufacturer's site for a known compatibility note on that Windows build.

## Root Cause
Windows feature updates sometimes replace or break OEM print drivers with a generic one, or hit a driver signature mismatch.

## Solution
1. Remove the printer entirely and reinstall using the latest driver from the manufacturer's site (not the one Windows Update installed).
2. If the manufacturer hasn't updated their driver yet, fall back to the Microsoft universal print driver as a temporary workaround.
3. Roll back the Windows update if it's a known-bad pairing and no fix is out yet.

## Verification
- Test page prints; Device Manager shows no error on the driver.

## Prevention
- Hold non-critical Windows feature updates a week or two on machines tied to specialized printers.

## Tags
`printer` `windows` `driver` `update`
