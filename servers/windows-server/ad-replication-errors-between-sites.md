# AD Replication Errors Between Sites

- **Category:** Server
- **OSI Layer:** 3 (Network, site-link transport)
- **Date documented:** 2026-06-30
- **Status:** Resolved

## Symptoms
- `repadmin /replsummary` shows failures between DCs at different sites
- Users see stale group memberships or intermittent auth failures

## Environment
- Number of sites/DCs, site link configuration, WAN connectivity between sites

## Diagnostic Steps
1. `repadmin /replsummary` on each DC to see which partner pairs are failing and the error code.
2. `repadmin /showrepl` for detailed error context (DNS lookup failure, RPC unavailable, access denied).
3. Check basic connectivity: can the DCs reach each other's required ports (RPC, DNS, Kerberos)?
4. Check DNS — replication depends heavily on correctly resolving each DC's SRV records.

## Root Cause
Most often a DNS resolution failure between sites, or a firewall blocking the RPC port range replication needs between DCs.

## Solution
1. Fix DNS first — confirm each DC points to a DNS server with the correct AD SRV records.
2. Open required ports between site DCs if blocked (RPC endpoint mapper, dynamic RPC range, LDAP/Kerberos/DNS).
3. Force a manual replication after fixing connectivity: `repadmin /syncall /AdeP`.
4. If the site link itself is misconfigured (wrong cost, overly restrictive schedule), correct it in Sites and Services.

## Verification
- `repadmin /replsummary` shows no errors across all DC pairs.

## Prevention
- Monitor replication health proactively.
- Document required firewall ports between sites.

## Tags
`server` `windows-server` `active-directory` `replication`
