# Battery Drains Rapidly

- **Category:** Hardware
- **OSI Layer:** N/A
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- Battery percentage drops fast even idle or asleep

## Environment
- Battery health %/cycle count
- Current OS power plan

## Diagnostic Steps
1. Run a battery report: `powercfg /batteryreport` (Windows) or `system_profiler SPPowerDataType` (macOS).
2. Check cycle count vs. design capacity in that report.
3. Check Task Manager/Activity Monitor for an app with high energy impact.
4. Confirm whether the drain happens during sleep — that points to a wake-lock or driver issue.

## Root Cause
Either an aged battery (capacity below ~80% of design after 2-3 years) or a background app/driver preventing proper sleep.

## Solution
1. If one app is the drain: update or replace it.
2. If draining during sleep: disable "wake on LAN"/USB wake settings in power options.
3. If battery health itself is degraded: this is hardware wear — replacement is the fix, not a setting.

## Verification
- Battery report shows a drain rate back in line with the battery's current health level.

## Prevention
- Avoid leaving the battery at 0% or 100% for long periods.
- Keep BIOS/firmware updated for power-management fixes.

## Tags
`laptop` `battery` `power-management`
