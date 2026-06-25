# Boot Loader / GRUB Failure

- **Category:** OS
- **OSI Layer:** N/A
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- System drops to a "GRUB rescue>" prompt
- Or boots past the OS into a black screen with a blinking cursor

## Environment
- Dual-boot or single-OS, whether a kernel update or disk change happened recently

## Diagnostic Steps
1. At the GRUB rescue prompt, `ls` to see if the boot partition is even visible to GRUB.
2. Boot a live USB and check `sudo fdisk -l` to confirm disk/partitions are intact.
3. Check whether this followed a kernel update where GRUB config wasn't regenerated.
4. Check whether another OS's installer overwrote the boot sector (common in dual-boot).

## Root Cause
Most commonly GRUB's configuration is out of sync with the actual partition layout, often after a kernel update or another OS overwriting the boot sector.

## Solution
1. Boot a live USB, mount the root partition, reinstall GRUB: `grub-install /dev/sdX` then `update-grub` (or `grub2-mkconfig` on RHEL-based systems).
2. If partitions moved, update `/etc/fstab` and GRUB's config references accordingly.
3. If a dual-boot Windows install overwrote the boot sector, reinstall GRUB last, then add a Windows entry via `os-prober`.

## Verification
- System reboots straight into a working GRUB menu and loads the OS normally.

## Prevention
- Re-run `update-grub` after kernel updates.
- Install GRUB last when dual-booting.

## Tags
`linux` `grub` `bootloader`
