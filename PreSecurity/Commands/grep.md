# grep

## Syntax
`grep [options] pattern [file(s)]`

## Purpose
Searches text using regular expressions. Filters lines matching a pattern from files or stdin.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-i` | Case-insensitive |
| `-r` or `-R` | Recursive directory search |
| `-n` | Show line numbers |
| `-v` | Invert match (show non-matching) |
| `-c` | Count matches |
| `-l` | List filenames with matches only |
| `-E` | Extended regex |
| `-o` | Show matched text only |
| `-A N` | Print N lines after match |
| `-B N` | Print N lines before match |

## Examples
```bash
grep "error" /var/log/syslog
grep -rni "password" /etc/
ps aux | grep apache
grep -E "192\.168\.\d+\.\d+" access.log
```

## Compatibility
Linux | Windows | macOS