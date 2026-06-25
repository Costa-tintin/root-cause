# Network Printer Not Found on New PC

- **Category:** Networking
- **OSI Layer:** 3-4 (Network / Transport)
- **Date documented:** 2026-05-25
- **Status:** Resolved

## Symptoms
- "Add Printer" doesn't discover it on a new PC, though other devices print fine

## Environment
- Subnet/VLAN of the new PC vs. the printer, network discovery settings

## Diagnostic Steps
1. Confirm the new PC and printer share a subnet/VLAN — mDNS/Bonjour discovery doesn't route across VLANs.
2. Check Network Discovery and Printer Sharing are enabled.
3. Try "The printer that I want isn't listed" > add by hostname/IP directly.
4. Ping the printer's IP from the new PC to confirm Layer 3 connectivity at least.

## Root Cause
Usually the new PC is on a different VLAN/subnet than the printer, and discovery protocols don't cross VLANs without a relay.

## Solution
1. Same subnet: enable Network Discovery and File/Printer Sharing on the PC.
2. Different subnet: add the printer manually by IP instead of relying on discovery.
3. For a permanent fix across VLANs: set up an mDNS reflector/relay, or standardize on add-by-IP for that printer.

## Verification
- Print job completes successfully from the new PC.

## Prevention
- Keep a central list of each network printer's static IP so it can always be added manually.

## Tags
`printer` `network` `vlan` `discovery`
