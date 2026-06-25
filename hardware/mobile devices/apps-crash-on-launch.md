# Apps Crash on Launch

- **Category:** Software
- **OSI Layer:** N/A
- **Date documented:** 2026-05-25
- **Status:** Resolved

## Symptoms
- App opens then immediately closes to the home screen
- Happens on one app, or several at once

## Environment
- OS version, app version, available storage

## Diagnostic Steps
1. Check available storage — under ~1GB free commonly causes crash-on-launch across apps.
2. Check whether the OS or the app was updated recently.
3. Force-stop and clear cache (Android) or offload/reinstall (iOS).
4. Note whether it's one app (app-specific bug) or many (points to OS/storage level).

## Root Cause
Usually low storage or a corrupted app cache after an update; if every app crashes at once, it's almost always storage or a botched OS update.

## Solution
1. Free up storage if low — clear caches, remove unused media.
2. Clear the app's cache/data, or delete and reinstall it.
3. If it's every app right after an OS update: check for pending app-store updates, since OS updates often break older app builds.

## Verification
- App launches and stays open through normal use.

## Prevention
- Keep at least 1-2GB free storage.
- Update apps promptly after OS updates.

## Tags
`mobile` `software` `app-crash`
