# Shows Offline Despite Being On

- **Category:** Networking
- **OSI Layer:** 3 (Network)
- **Date documented:** 2026-05-25
- **Status:** Resolved

## Symptoms
- Print queue shows "Offline"
- Printer's own display shows ready/idle

## Environment
- Connection type (USB / network / Wi-Fi), printer's IP if networked

## Diagnostic Steps
1. `ping <printer-ip>` from the PC.
2. Check whether the printer's IP changed recently (common with plain DHCP, no reservation).
3. In Windows: Printer Properties > Ports — confirm the port IP matches the printer's current IP.
4. Check that "Use Printer Offline" hasn't been toggled on manually.

## Root Cause
Most commonly DHCP reassigned the printer a new IP, leaving the PC's saved port pointing at the old address.

## Solution
1. Set a DHCP reservation for the printer's MAC address so its IP never changes.
2. Update the port IP in Windows to match the current address, or delete and re-add the printer.
3. Restart the print spooler: `net stop spooler && net start spooler`.

## Verification
- Status changes to "Ready" and a test page prints.

## Prevention
- Always set a DHCP reservation for network printers.

## Tags
`printer` `network` `offline` `dhcp`
