# Permission Errors on Shared Folder

- **Category:** OS
- **OSI Layer:** N/A
- **Date documented:** 2026-06-25
- **Status:** Resolved

## Symptoms
- "Permission denied" accessing a shared folder over Samba/NFS, or even locally as the file owner

## Environment
- Filesystem type, sharing method (Samba/NFS), user/group involved

## Diagnostic Steps
1. `ls -la` on the folder to check actual owner, group, and permission bits.
2. `id <username>` to confirm the user is in the expected group.
3. For Samba: `testparm`, and check `smb.conf` for the share's valid users/write list.
4. For NFS: check `/etc/exports` for the correct client IP/subnet and ro/rw flags.

## Root Cause
Most often the user isn't in the group the folder's permissions expect, or the share config restricts access more tightly than intended.

## Solution
1. Add the user to the correct group: `usermod -aG <group> <username>`, then have them re-login.
2. Fix folder permissions: `chmod 770 <folder>` and `chgrp <group> <folder>`.
3. Samba: correct valid users/write list in `smb.conf`, then `systemctl restart smb`.
4. NFS: fix the export line in `/etc/exports`, then `exportfs -ra`.

## Verification
- The affected user can read/write the share without error.

## Prevention
- Use group-based permissions consistently rather than per-user ACLs that are easy to lose track of.

## Tags
`linux` `permissions` `samba` `nfs`
