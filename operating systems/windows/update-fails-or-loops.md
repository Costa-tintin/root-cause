# Windows Update Fails or Loops

- **Category:** OS
- **OSI Layer:** N/A
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- Update fails with an error code and retries endlessly
- PC reboots into "Working on updates" repeatedly without completing

## Environment
- Windows build, free disk space, cumulative vs feature update

## Diagnostic Steps
1. Note the exact error code from Settings > Windows Update > Update history.
2. Check free disk space — updates can need 5-20GB temporarily.
3. Run the built-in Windows Update Troubleshooter.
4. Check `C:\Windows\Logs\CBS\CBS.log` for the specific failing component if the troubleshooter doesn't resolve it.

## Root Cause
Most commonly insufficient disk space, a corrupted update cache, or a stuck Windows Update service.

## Solution
1. Free up disk space if low.
2. Stop the Windows Update service, clear the SoftwareDistribution folder, restart the service.
3. Run `sfc /scannow` and `DISM /Online /Cleanup-Image /RestoreHealth` to repair system files.
4. If a feature update specifically fails: download and run the standalone installer from Microsoft directly.

## Verification
- Update installs successfully; Windows Update shows "You're up to date."

## Prevention
- Keep at least 20GB free disk space.
- Don't let updates queue for months before installing.

## Tags
`windows` `os` `update`
