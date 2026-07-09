# traceroute / tracert

## Syntax
`traceroute [options] destination` (Linux/macOS)
`tracert destination` (Windows)

## Purpose
Maps the path packets take from source to destination, showing each hop (router).

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-n` | Show IP addresses only (no DNS resolution) |
| `-m N` | Set max TTL (max hops) |
| `-p N` | Set destination port (Linux) |
| `-w N` | Wait N seconds per reply |

## Examples
```bash
traceroute google.com
traceroute -n tryhackme.com
tracert 10.10.10.1
```

## Compatibility
Linux | Windows | macOS