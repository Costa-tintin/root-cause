# Service Won't Start After Reboot

- **Category:** Server
- **OSI Layer:** N/A
- **Date documented:** 2026-06-30
- **Status:** Resolved

## Symptoms
- A critical service (SQL Server, IIS, a custom app) shows "Stopped" after a reboot and won't start manually either

## Environment
- Windows Server version, service account used, dependent services

## Diagnostic Steps
1. Try starting it manually via `services.msc` and note the exact error.
2. Check Event Viewer > System and Application logs for the startup failure entry.
3. Check the service's dependencies: `sc qc <servicename>`.
4. Confirm the service account's password hasn't expired/changed.

## Root Cause
Most often a dependent service failed first, or the service account's credentials are no longer valid.

## Solution
1. Start dependency services first in the correct order, then retry this one.
2. If the account password expired: reset it and update the service's logon credentials.
3. If config-related: check for a path/setting that changed, e.g. a drive letter that shifted after reboot.

## Verification
- Service starts automatically on the next reboot and stays running.

## Prevention
- Use a non-expiring managed service account.
- Document service dependency order.

## Tags
`server` `windows-server` `service`
