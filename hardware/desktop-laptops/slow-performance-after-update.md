# Slow Performance After Update

- **Category:** OS
- **OSI Layer:** N/A
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- Noticeably slower boot/app load right after an OS or driver update
- High disk or CPU usage while idle

## Environment
- OS build before/after the update
- Storage type — HDD vs SSD

## Diagnostic Steps
1. Open Task Manager/Activity Monitor sorted by CPU and Disk to find a runaway process.
2. Check Windows Update history for what changed.
3. Check Reliability Monitor for crashes that line up with the update.
4. Confirm free disk space — under ~10-15% slows SSD TRIM/garbage collection.

## Root Cause
Usually a background re-indexing pass (Windows Search/Superfetch) right after the update, or occasionally a buggy driver the update pushed.

## Solution
1. Let post-update indexing finish — check Windows Search indexing status, it can take a few hours.
2. Restart the SysMain (Superfetch) service if it's stuck at high disk usage.
3. Roll back any driver flagged in Reliability Monitor.
4. Free up disk space to at least 10-15% if on an SSD.

## Verification
- CPU/disk usage returns to baseline at idle; boot time back to normal.

## Prevention
- Check free disk space before major updates.
- Delay non-critical driver updates a few days after release.

## Tags
`laptop` `windows` `performance` `update`
