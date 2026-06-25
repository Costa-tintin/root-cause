# Overheating / Fan Running Constantly

- **Category:** Hardware
- **OSI Layer:** N/A
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- Fan at full speed even while idle
- Hot to the touch near vents
- CPU clock drops under load (thermal throttling)

## Environment
- Ambient temperature, laptop age
- Whether vents look dusty or airflow is obstructed

## Diagnostic Steps
1. Check temps with HWMonitor or `sensors` (Linux) at idle and under load.
2. Check Task Manager for a runaway process — malware can cause this too.
3. Inspect intake vents for dust buildup.
4. Check whether the laptop is sitting on a soft surface blocking intake.

## Root Cause
Most often a dust-clogged heatsink/fan or dried thermal paste; less commonly a stuck background process.

## Solution
1. If software-caused: end/uninstall the runaway process.
2. Power off and clean vents/fan with compressed air.
3. If idle temps are still high after cleaning: repaste the CPU/GPU (requires opening the chassis).
4. Use a hard, elevated surface to improve intake airflow.

## Verification
- Idle temps drop to a normal range (typically under 50°C) and the fan throttles down at idle.

## Prevention
- Clean vents every 6-12 months.
- Avoid blocking intake on soft surfaces.

## Tags
`laptop` `hardware` `thermal` `fan`
