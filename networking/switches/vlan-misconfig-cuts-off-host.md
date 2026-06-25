# VLAN Misconfiguration Cuts Off a Host

- **Category:** Networking
- **OSI Layer:** 2-3 (Data Link / Network)
- **Date documented:** 2026-01-1
- **Status:** Resolved

## Symptoms
- One host can't reach anything, including its own gateway, after a switch change

## Environment
- Intended VLAN for that host, upstream trunk configuration

## Diagnostic Steps
1. `show running-config interface <port>` — confirm access VLAN matches what's intended.
2. `show vlan brief` — confirm that VLAN actually exists on this switch.
3. If through a trunk: `show interfaces trunk` — confirm the VLAN is allowed across it.
4. Check the host's IP/subnet matches the VLAN's actual subnet.

## Root Cause
Typically the access port was assigned to a VLAN that doesn't exist on that switch, or isn't permitted across the upstream trunk.

## Solution
1. Create the VLAN if missing: `vlan <id>` then `name <name>`.
2. Set the correct access VLAN: `switchport access vlan <id>`.
3. If trunked: `switchport trunk allowed vlan add <id>`.
4. Correct the host's IP configuration if it doesn't match the VLAN's subnet.

## Verification
- Host can ping its gateway and reach other hosts in its VLAN.

## Prevention
- Keep a VLAN-to-subnet mapping doc.
- Verify trunk allowed-VLAN lists whenever adding a new VLAN.

## Tags
`switch` `network` `vlan` `trunk`
