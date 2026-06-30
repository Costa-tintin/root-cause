# Backup Job Fails Silently

- **Category:** Server
- **OSI Layer:** N/A
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- Scheduled backup hasn't produced a new file in days, with no alert fired

## Environment
- Backup method (cron + rsync/tar, or a tool), where output/errors are logged

## Diagnostic Steps
1. Check the cron log to confirm the job is even firing on schedule.
2. Manually run the backup script in the foreground to see if it errors immediately.
3. Check destination storage isn't full or unreachable.
4. Check the script doesn't depend on an environment variable or PATH that cron doesn't have.

## Root Cause
Most often a cron environment difference — the script works manually but fails under cron from a missing PATH/env variable, or the destination ran out of space/became unreachable.

## Solution
1. Set explicit full paths for all commands inside the backup script.
2. Redirect the script's output/errors to a log file directly from the crontab line.
3. Add a basic success check at the end of the script that alerts if the backup wasn't created or is unexpectedly small.
4. Free up or fix connectivity to the destination if that was the cause.

## Verification
- Next scheduled run produces a fresh, correctly-sized backup file, confirmed in the log.

## Prevention
- Always log cron job output.
- Add a basic alert-on-failure check rather than assuming silence means success.

## Tags
`server` `linux-server` `backup` `cron`
