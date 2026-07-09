# chown

**Change Owner** — a command-line utility that changes the user and/or group ownership of files and directories.

## Syntax

```
chown [options] <owner>[:<group>] <file...>
```

## Purpose

Transfer file or directory ownership to another user or group. Critical for system administration — proper ownership ensures only authorized users can access or modify files. Often required after copying files between accounts or setting up shared resources.

## Parameters

| Parameter | Description |
|-----------|-------------|
| `-R` | Recursive (apply to all files/dirs) |
| `-v` | Verbose (show changes) |
| `-c` | Report only when a change is made |
| `--reference=<file>` | Copy ownership from another file |
| `--from=<owner>[:<group>]` | Only change if current owner/group matches |
| `-h` | Affect symbolic links, not their targets |
| `-f` | Suppress most error messages |

## Ownership Notation

| Notation | Effect |
|----------|--------|
| `chown alice file` | Change owner to `alice` |
| `chown alice:admins file` | Change owner to `alice` and group to `admins` |
| `chown :admins file` | Change group to `admins` only |
| `chown alice: file` | Change owner to `alice` and group to alice's primary group |

## Examples

```bash
# Change file owner
sudo chown alice file.txt

# Change owner and group
sudo chown alice:admins file.txt

# Change group only
sudo chown :www-data /var/www/html/index.html

# Recursively change ownership of a directory
sudo chown -R alice:users /home/alice/

# Change owner only if currently owned by bob
sudo chown --from=bob alice file.txt

# Copy ownership from another file
sudo chown --reference=template.txt target.txt

# Verbose recursive change
sudo chown -Rv alice:alice /home/alice/

# Change ownership of symlink (not target)
sudo chown -h alice link_file

# Set owner to UID 1000 (works even if user doesn't exist)
sudo chown 1000:1000 file.txt
```

## Common Mistakes

- Forgetting `sudo` — only root can change ownership of files they do not own.
- Using `chown` instead of `chgrp` for group-only changes — `chown :group` works but `chgrp` is clearer.
- Changing system file ownership — can break services or make the system non-bootable.
- Not using `-R` on directories — the directory's ownership changes but the files inside retain the old owner.
- Changing ownership of mounted filesystems — may not be supported by the underlying filesystem (e.g., FAT32, NTFS).
- Assuming you can change ownership of files you own — only root can assign ownership to another user.

## Real-World Usage

- **User management:** After creating a new user, change ownership of their home directory: `chown -R alice:alice /home/alice/`.
- **Web server setup:** Ensure web files are owned by the correct user (e.g., `www-data`):
  `sudo chown -R www-data:www-data /var/www/html`.
- **CTF challenges:** Enumerate files owned by specific users, identify misconfigured ownership for privilege escalation.
- **Service migrations:** When moving data between systems, fix ownership to match the new environment.
- **Shared directories:** Set a common group and ensure all members can access files.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (GNU coreutils) |
| Windows | Limited | Via WSL, or use `takeown` / `icacls` |
| macOS | Full | Pre-installed (BSD version, slightly different flags) |

```bash
# chown is pre-installed on all Linux/macOS systems
```
