# NAT/PAT Not Translating Outbound Traffic

- **Category:** Networking
- **OSI Layer:** 3-4 (Network / Transport)
- **Date documented:** 2026-01-1
- **Status:** Resolved

## Symptoms
- Internal hosts can't reach the internet despite a valid WAN IP
- `show ip nat translations` is empty

## Environment
- NAT type configured (static, dynamic, PAT/overload), interfaces involved

## Diagnostic Steps
1. `show ip nat statistics` — confirms NAT is active and which interfaces are inside/outside.
2. Confirm `ip nat inside` is on the LAN interface(s) and `ip nat outside` on the WAN interface.
3. Check the NAT access-list actually matches the internal subnet needing translation.
4. For subinterfaces: confirm `ip nat inside` is applied to each one individually, not just the parent interface.

## Root Cause
Almost always a missing `ip nat inside`/`ip nat outside` statement on an interface, or a NAT ACL that doesn't match the real internal subnet.

## Solution
1. Apply `ip nat inside` on every LAN-facing interface/subinterface, `ip nat outside` on the WAN interface.
2. Fix the NAT ACL to match the actual internal subnet(s).
3. For PAT/overload: confirm `ip nat inside source list <acl> interface <wan-if> overload` references the correct interface and ACL.

## Verification
- `show ip nat translations` populates with active sessions when a LAN host browses the internet.

## Prevention
- When adding new VLANs/subinterfaces, checklist includes applying NAT inside on each one.

## Tags
`router` `network` `nat` `pat`
