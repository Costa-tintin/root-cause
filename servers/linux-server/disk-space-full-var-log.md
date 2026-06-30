# Disk Space Full (/var/log)

- **Category:** Server
- **OSI Layer:** N/A
- **Date documented:** 2026-06-30
- **Status:** Resolved

## Symptoms
- Low disk space alerts; services failing to write logs/data
- `df -h` shows root or /var near 100%

## Environment
- Distro, logging setup (journald, rsyslog, app logs), whether log rotation is configured

## Diagnostic Steps
1. `df -h` to confirm which partition is full.
2. `du -sh /var/log/*` to find the largest log files/directories.
3. Check logrotate is configured and actually running.
4. `journalctl --disk-usage` if using systemd journal — it can grow unbounded without a size cap.

## Root Cause
Almost always log rotation either isn't configured for a specific service or has silently stopped running.

## Solution
1. Manually truncate or compress the oversized log to free immediate space.
2. Add or fix a logrotate config for the offending service with sane size/age limits.
3. Cap the systemd journal size (`SystemMaxUse=500M` in `/etc/systemd/journald.conf`), then restart journald.

## Verification
- Disk usage drops to a safe level and stays stable over the next few days with rotation in place.

## Prevention
- Set disk usage alerting well before 100% (e.g. at 80%).
- Verify logrotate runs after deploying any new service.

## Tags
`server` `linux-server` `disk-space` `logging`
