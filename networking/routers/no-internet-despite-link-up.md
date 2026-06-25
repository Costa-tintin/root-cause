# No Internet Despite Link Up

- **Category:** Networking
- **OSI Layer:** 3 (Network)
- **Date documented:** 2026-01-1
- **Status:** Resolved

## Symptoms
- Link lights active, LAN devices get an IP, but no internet access

## Environment
- WAN connection type (DHCP/PPPoE/static from ISP), router model

## Diagnostic Steps
1. `show ip interface brief` — confirm the WAN interface has a valid ISP-assigned IP.
2. Ping the ISP gateway directly from the router.
3. Ping a public IP (e.g. 8.8.8.8) vs a domain name to separate routing from DNS.
4. Confirm NAT/PAT is configured and active on the WAN interface.

## Root Cause
Commonly either the WAN side hasn't pulled a valid IP from the ISP (modem/ONT issue or PPPoE auth failure), or NAT isn't translating outbound traffic.

## Solution
1. If no WAN IP: power-cycle the modem/ONT then the router; recheck PPPoE credentials if applicable.
2. If WAN IP is valid but no NAT: reapply `ip nat outside` on WAN and `ip nat inside` on LAN interfaces.
3. If IP pings work but domains don't: fix the DNS server settings being pushed via DHCP.

## Verification
- LAN device can ping a public IP and resolve a domain name successfully.

## Prevention
- Document ISP connection type/credentials.
- Monitor WAN IP for unexpected loss.

## Tags
`router` `network` `wan` `nat`
