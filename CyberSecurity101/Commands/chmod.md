# chmod

**Change Mode** — a command-line utility that changes the file system permissions (mode) of files and directories.

## Syntax

```
chmod [options] <mode> <file...>
```

## Purpose

Set read, write, and execute permissions for the file owner, group, and others. Critical for system security — incorrect permissions can expose sensitive files or allow unauthorized execution.

## Permission Modes

### Symbolic Mode

| Symbol | Meaning |
|--------|---------|
| `u` | User (owner) |
| `g` | Group |
| `o` | Others |
| `a` | All (ugo) |
| `+` | Add permission |
| `-` | Remove permission |
| `=` | Set exact permission |
| `r` | Read |
| `w` | Write |
| `x` | Execute |

### Numeric (Octal) Mode

| Octal | Binary | Permissions |
|-------|--------|-------------|
| `0` | `000` | `---` |
| `1` | `001` | `--x` |
| `2` | `010` | `-w-` |
| `3` | `011` | `-wx` |
| `4` | `100` | `r--` |
| `5` | `101` | `r-x` |
| `6` | `110` | `rw-` |
| `7` | `111` | `rwx` |

Common modes: `755` (rwxr-xr-x), `644` (rw-r--r--), `600` (rw-------), `777` (rwxrwxrwx).

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-R` | Recursive (apply to all files/dirs) |
| `-v` | Verbose (show changes) |
| `-c` | Like verbose but report only when change is made |
| `--reference=<file>` | Copy permissions from another file |
| `-f` | Suppress most error messages |

## Examples

```bash
# Add execute permission for all
chmod +x script.sh

# Set owner to read/write, group and others to read-only
chmod 644 file.txt

# Give full permissions to owner only
chmod 600 private.key

# Standard executable permissions
chmod 755 program.py

# Recursively set directory permissions
chmod -R 755 /var/www/html

# Add write permission for group
chmod g+w file.txt

# Remove execute permission for others
chmod o-x file.txt

# Set setuid bit (dangerous — elevates privileges)
chmod u+s program

# Set sticky bit (only owner can delete files in directory)
chmod +t /tmp/shared

# Copy permissions from reference file
chmod --reference=template.txt target.txt

# Set all to read and write, recursive
chmod -R a+rw /tmp/shared
```

## Common Mistakes

- Using `chmod 777` on everything — makes files world-writable. Never use `777` for security-sensitive files.
- Forgetting `-R` on directories — permissions only apply to the directory, not its contents.
- Setting execute permission on text files — unnecessary and a potential vector for accidental execution.
- Using `chmod 777` on SSH keys — SSH requires `600` on private keys, `755` on `~/.ssh`.
- Changing permissions on system files without understanding consequences — can break the system.
- Not realizing that directory execute permission (`x`) is needed to `cd` into it and access its contents.

## Real-World Usage

- **CTF privilege escalation:** Find and exploit SUID binaries, writable scripts, or misconfigured permissions.
- **Server hardening:** Ensure configuration files are not world-readable, scripts are not world-writable.
- **Web security:** Set proper permissions on web directories (`755`) and files (`644`).
- **Key management:** Restrict SSH private key permissions to `600`.
- **Shared directories:** Use sticky bit (`+t`) on `/tmp` to prevent users from deleting each other's files.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (GNU coreutils) |
| Windows | N/A | Use `icacls` for NTFS permissions |
| macOS | Full | Pre-installed (BSD version) |

```bash
# chmod is pre-installed on all Linux/macOS systems
```
