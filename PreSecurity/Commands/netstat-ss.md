# netstat / ss

## Syntax
`netstat [options]` (older) `ss [options]` (modern Linux replacement)

## Purpose
Display network connections, routing tables, interface statistics, and listening ports.

## Common Parameters (netstat)

| Parameter | Description |
|-----------|-------------|
| `-t` | TCP connections |
| `-u` | UDP connections |
| `-l` | Listening sockets |
| `-n` | Show numeric addresses/ports |
| `-p` | Show PID/program name |
| `-a` | All connections (listening + established) |
| `-r` | Show routing table |

## Common Parameters (ss)

| Parameter | Description |
|-----------|-------------|
| `-t` | TCP |
| `-u` | UDP |
| `-l` | Listening |
| `-n` | Numeric |
| `-p` | Process information |
| `-a` | All |
| `-s` | Summary statistics |

## Examples
```bash
netstat -tuln
netstat -tulnp
ss -tuln
ss -tup
```

## Compatibility
Linux (both) | macOS (netstat only)