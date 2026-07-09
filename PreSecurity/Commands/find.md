# find

## Syntax
`find [path] [expression]`

## Purpose
Searches for files/directories in a directory hierarchy based on name, type, size, permissions, modification time, etc.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-name PATTERN` | Match filename (case-sensitive) |
| `-iname PATTERN` | Match filename (case-insensitive) |
| `-type f` | Files only |
| `-type d` | Directories only |
| `-size +10M` | Larger than 10 MB |
| `-mtime -N` | Modified within N days |
| `-perm MODE` | Match permissions |
| `-user USER` | Owned by user |
| `-exec CMD {} \;` | Run command on each result |
| `-delete` | Delete matched files |

## Examples
```bash
find /var/log -name "*.log" -mtime -7
find / -type f -perm 4000 2>/dev/null
find /home -size +100M
find /tmp -name "*.php" -exec rm {} \;
```

## Compatibility
Linux | macOS