# Blue Screen / Kernel Panic on Startup

- **Category:** OS
- **OSI Layer:** N/A
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- BSOD with a stop code (e.g. DRIVER_IRQL_NOT_LESS_OR_EQUAL)
- Or a kernel panic trace on Linux/macOS at boot

## Environment
- OS version, and whether a driver/update was installed just before this started

## Diagnostic Steps
1. Note the exact stop code or panic message.
2. Boot into Safe Mode (Windows) or recovery mode.
3. Check Event Viewer > Windows Logs > System for the faulting driver.
4. On Linux, check `journalctl -xb -1` for the panic trace from the previous boot.

## Root Cause
Almost always a recently updated driver (GPU, Wi-Fi, storage controller) or a corrupted system file.

## Solution
1. Uninstall or roll back the offending driver from Safe Mode.
2. Run `sfc /scannow` then `DISM /Online /Cleanup-Image /RestoreHealth` (Windows).
3. If it started right after a Windows update, use System Restore to a point before it.
4. On Linux, boot the previous kernel from GRUB, then remove the bad package.

## Verification
- Clean boot to desktop with no recurrence across 2-3 restarts.

## Prevention
- Stagger driver updates instead of installing all at once.
- Keep a System Restore point before major updates.

## Tags
`laptop` `windows` `bsod` `driver`
