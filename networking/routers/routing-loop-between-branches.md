# Routing Loop Between Branches

- **Category:** Networking
- **OSI Layer:** 3 (Network)
- **Date documented:** 2026-01-1
- **Status:** Resolved

## Symptoms
- Traffic between two branch sites never arrives
- TTL expires in transit
- Intermittent total outage between sites

## Environment
- Routing protocol in use (static, OSPF, BGP), number of paths between branches

## Diagnostic Steps
1. `traceroute` from one branch to the other — a repeating hop pattern indicates the loop.
2. `show ip route` at each hop — look for a route pointing back the way traffic came.
3. If OSPF: `show ip ospf neighbor` and review area design — a misconfigured ABR or area mismatch on a WAN link is a common cause.
4. If static routes: check for two routers each pointing the destination network at the other as next-hop.

## Root Cause
Most often a routing protocol area/redistribution misconfiguration (e.g. a WAN link placed in Area 0 instead of its branch area), or conflicting static routes.

## Solution
1. For OSPF: correct the area assignment on the WAN link to match its branch's area, not Area 0, unless that router is genuinely the ABR.
2. For static routing: remove the conflicting route, or replace with a proper dynamic routing protocol.
3. After the fix, clear the route cache and re-verify with traceroute before declaring it resolved.

## Verification
- Traceroute shows a clean, finite path between branches with no repeating hops.

## Prevention
- Document the intended area design before deploying.
- Avoid static routes as a permanent fix once dynamic routing is in place.

## Tags
`router` `network` `routing-loop` `ospf`
