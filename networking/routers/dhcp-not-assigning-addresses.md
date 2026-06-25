# DHCP Not Assigning Addresses

- **Category:** Networking
- **OSI Layer:** 3 (Network)
- **Date documented:** 2026-01-1
- **Status:** Resolved

## Symptoms
- Devices get no IP (APIPA 169.254.x.x on Windows), or "obtaining IP address" hangs

## Environment
- DHCP server location (router itself or separate server), VLAN/subnet involved

## Diagnostic Steps
1. `show ip dhcp pool` — confirm the pool exists and isn't exhausted.
2. `show ip dhcp conflict` — check for IP conflicts blocking leases.
3. Check `ip dhcp excluded-address` ranges don't accidentally cover the whole usable pool.
4. Confirm `ip helper-address` is configured if the DHCP server sits on a different VLAN.

## Root Cause
Most often an exhausted pool, a misconfigured excluded-address range, or a missing DHCP relay across VLANs.

## Solution
1. If pool exhausted: expand the subnet/pool or shorten lease times.
2. If excluded-address range is wrong: rebuild the pool from scratch — overlapping excludes are easy to miss.
3. If cross-VLAN: add `ip helper-address <dhcp-server-ip>` on the VLAN interface.

## Verification
- Client receives a valid IP in the expected range within seconds of requesting.

## Prevention
- Monitor pool utilization.
- Document excluded ranges clearly in config comments.

## Tags
`router` `network` `dhcp`
