# OSI Layer Quick-Reference

Tag every networking issue with the layer it actually belongs to — this is the
detail that makes the networking folder read as methodical rather than just
"a list of fixes."

| Layer | Common Problems | First Checks |
|---|---|---|
| 7 — Application | DNS resolution, app config, browser errors | nslookup, app logs, clear cache |
| 6 — Presentation | TLS/SSL cert errors, encoding mismatches | Check cert validity, openssl s_client |
| 5 — Session | VPN/RDP session drops, timeouts | Session logs, timeout settings |
| 4 — Transport | Blocked ports, firewall rules | telnet/nc to port, netstat -an |
| 3 — Network | IP conflicts, bad subnetting, routing | ping, traceroute, show ip route |
| 2 — Data Link | VLAN mismatch, STP loops, MAC issues | show mac address-table, show spanning-tree |
| 1 — Physical | Bad cable, dead port, no power (PoE) | Link lights, cable tester, show interfaces |

Working top-down (7→1) suits application complaints ("the site won't load").
Working bottom-up (1→7) suits hardware-flavored complaints ("the whole branch
is down"). Note which direction you used in the diagnostic steps — it shows
the reasoning, not just the fix.
