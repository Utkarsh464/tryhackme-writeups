# chmod

## Syntax
`chmod [options] mode file(s)`

## Purpose
Changes file/directory permissions (read, write, execute) for owner, group, and others.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-R` | Recursive |
| `+x` | Add execute |
| `-r` | Remove read |
| `u=rwx,g=rx,o=r` | Explicit mode |
| `755` | Numeric mode (rwxr-xr-x) |
| `644` | Numeric mode (rw-r--r--) |
| `600` | Numeric mode (rw-------) |

## Examples
```bash
chmod +x script.sh
chmod 755 script.sh
chmod -R 600 private/
chmod u=rw,g=r,o= file.txt
```

## Compatibility
Linux | macOS