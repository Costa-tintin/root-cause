# Print Jobs Stuck in Queue

- **Category:** OS
- **OSI Layer:** N/A
- **Date documented:** 2026-05-25
- **Status:** Resolved

## Symptoms
- Jobs sit at "Printing" and never complete
- Queue won't clear even after Cancel

## Environment
- Print Spooler service status, file types being printed

## Diagnostic Steps
1. Check job status in the print queue — paused, error, or no error shown.
2. Check the Print Spooler service in `services.msc`.
3. Check the spool folder for an oversized/corrupted file: `C:\Windows\System32\spool\PRINTERS`.
4. Confirm the printer itself isn't paused/in an error state at the device.

## Root Cause
Usually a corrupted spool file from a previous job stuck the queue, or the spooler service hung.

## Solution
1. Stop the Print Spooler service, delete all files in spool\PRINTERS, restart the service.
2. Cancel all queued jobs before restarting the spooler — stuck jobs can re-queue otherwise.
3. If this recurs often, update or reinstall the printer driver — outdated drivers commonly corrupt spool files.

## Verification
- A new test print completes and the queue clears normally.

## Prevention
- Keep the printer driver current.
- Confirm the printer is online before sending very large jobs.

## Tags
`printer` `windows` `spooler` `queue`
