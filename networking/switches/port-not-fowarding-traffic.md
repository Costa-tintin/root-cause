# STP Loop / Broadcast Storm

- **Category:** Networking
- **OSI Layer:** 2 (Data Link)
- **Date documented:** 2026-01-1
- **Status:** Resolved

## Symptoms
- Network-wide slowness or total outage
- Switch port LEDs flashing rapidly
- CPU usage spikes on switches

## Environment
- Topology — any redundant links between switches? STP mode in use (PVST/RSTP/MST)

## Diagnostic Steps
1. `show spanning-tree` on each switch — look for ports flapping between blocking/forwarding.
2. Check for a recently added redundant link, or an unmanaged switch looped back into the network.
3. `show interfaces counters` — an interface with a huge, fast-climbing packet count points to the loop source.
4. Confirm STP is actually enabled on every switch in the path, not just the core.

## Root Cause
Almost always a redundant physical link between switches without STP converging properly, frequently from an unmanaged switch plugged into two ports.

## Solution
1. Physically disconnect the suspected loop link immediately to stop the storm.
2. Confirm STP/RSTP is enabled network-wide.
3. Re-add the redundant link only after `show spanning-tree` confirms one path forwarding, one blocking.
4. Enable BPDU Guard on access ports to prevent this from happening again via an unmanaged switch.

## Verification
- Switch CPU returns to normal; `show spanning-tree` shows a stable topology with no flapping.

## Prevention
- Enable BPDU Guard on all access ports.
- Label/document any intentional redundant links.

## Tags
`switch` `network` `stp` `loop`
