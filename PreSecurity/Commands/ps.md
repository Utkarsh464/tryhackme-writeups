# ps

## Syntax
`ps [options]`

## Purpose
Displays information about running processes. Commonly used with aux or ef flags for a full view.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `aux` | Show all processes (BSD syntax) |
| `ef` | Show full-format listing (standard syntax) |
| `-u USER` | Show processes for a user |
| `-C name` | Show processes by command name |
| `-f` | Full-format listing |
| `--sort` | Sort output (e.g., `-%mem`, `-%cpu`) |

## Examples
```bash
ps aux
ps aux | grep apache
ps -ef --forest
ps -u www-data
ps aux --sort=-%mem | head
```

## Compatibility
Linux | macOS