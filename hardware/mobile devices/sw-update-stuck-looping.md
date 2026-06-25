# Software Update Stuck / Looping

- **Category:** Software
- **OSI Layer:** N/A
- **Date documented:** 2026-05-25
- **Status:** Resolved

## Symptoms
- Update progress bar stuck for a long time
- Or device reboots into the update process repeatedly

## Environment
- OS version, available storage, Wi-Fi vs cellular for the download

## Diagnostic Steps
1. Check available storage — updates need free space roughly equal to the update size.
2. Confirm Wi-Fi is stable and not dropping mid-download.
3. Let it sit through the manufacturer's stated max time before forcing anything.
4. Check the device isn't critically low on battery, which some OSes block updates over.

## Root Cause
Usually insufficient free storage or an interrupted download/install from unstable Wi-Fi.

## Solution
1. If genuinely stuck past the expected window: force restart using the device's button combo.
2. Free up storage and retry the update.
3. If it loops on every boot: use recovery mode to sideload the update or restore via the manufacturer's desktop tool.
4. As a last resort, factory reset after backing up data — a persistent loop can indicate a corrupted system partition.

## Verification
- Device completes the update and boots normally to the home screen.

## Prevention
- Keep at least 2x the update size free in storage.
- Update over stable Wi-Fi with the device plugged in.

## Tags
`mobile` `software` `update-loop`
