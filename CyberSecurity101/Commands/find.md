# find

**Find** — a command-line utility for searching files in a directory hierarchy based on various criteria.

## Syntax

```
find <path> [expression] [actions]
```

## Purpose

Locate files and directories based on name, type, size, permissions, modification time, ownership, and other attributes. Essential for system administration, CTF challenges, and penetration testing when searching for specific files or misconfigurations.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-name <pattern>` | Match filename (case-sensitive) |
| `-iname <pattern>` | Match filename (case-insensitive) |
| `-type f` | Regular files only |
| `-type d` | Directories only |
| `-size <n>` | File size (`+100M`, `-1G`, `500k`, `1024c`) |
| `-mtime <n>` | Modification time in days (`-7` = last 7 days) |
| `-mmin <n>` | Modification time in minutes |
| `-perm <mode>` | Permission mode (`/4000` = SUID, `-o=x` = executable) |
| `-user <user>` | Owner username |
| `-group <group>` | Group name |
| `-exec <cmd> {} \;` | Execute command on matched files |
| `-ok <cmd> {} \;` | Same as exec but prompts for confirmation |
| `-delete` | Delete matched files |
| `-print` | Print results (default) |
| `-maxdepth <N>` | Limit directory depth |
| `-mindepth <N>` | Minimum directory depth |

## Examples

```bash
# Find files by name
find /home -name "flag.txt"

# Find files by extension (case-insensitive)
find /var/www -iname "*.php"

# Find directories
find / -type d -name "admin"

# Find files larger than 100MB
find / -type f -size +100M

# Find files modified in the last 7 days
find /etc -mtime -7

# Find files with SUID bit set (privilege escalation)
find / -perm -4000 -type f 2>/dev/null

# Find files with write permission for "other" (world-writable)
find / -perm -o=w -type f 2>/dev/null

# Find and delete .tmp files
find /tmp -name "*.tmp" -delete

# Find and execute command on each file
find /var/log -name "*.log" -exec grep -l "error" {} \;

# Find empty files
find / -type f -empty

# Combine criteria
find / -type f -name "*.conf" -user root -size -10k

# Find files with SGID bit set
find / -perm -2000 -type f 2>/dev/null
```

## Common Mistakes

- Not limiting depth with `-maxdepth` on large filesystems — scans the entire tree and takes forever.
- Forgetting `2>/dev/null` — permission denied errors clutter output when searching `/` as a regular user.
- Using `-delete` without testing first — always run without `-delete` first to preview matches.
- Not quoting patterns with wildcards — `find / -name *.txt` expands the glob in the current directory before find runs.
- Using `-exec` without `{} \;` — the syntax is strict; missing semicolon or braces will fail.
- Running find on network mounts — NFS/CIFS mounts are slow and may cause hangs.

## Real-World Usage

- **Privilege escalation (CTF):** Find SUID binaries (`find / -perm -4000`), world-writable files, or scripts owned by root.
- **File discovery:** Locate configuration files, password dumps, backup files, or hidden directories.
- **Cleanup:** Find and remove old log files, temporary files, or core dumps.
- **Compliance checking:** Identify files with insecure permissions across a filesystem.
- **Forensics:** Locate files modified during a specific time window after an incident.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (GNU find) |
| Windows | Limited | `dir /s` or `where`, or use WSL |
| macOS | Full | Pre-installed (BSD find, similar syntax) |

```bash
# Install on Linux (pre-installed)
# find is part of findutils
sudo apt install findutils
```
