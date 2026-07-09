# ping

## Syntax
`ping [options] destination`

## Purpose
Tests reachability and measures round-trip time to a network host.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-c N` | Send N packets (Linux) |
| `-n N` | Send N packets (Windows) |
| `-i N` | Interval in seconds between pings |
| `-t` | Ping continuously (Windows) |
| `-4` | Force IPv4 |

## Examples
```bash
ping -c 4 google.com
ping -c 1 10.10.10.1
ping -n 10 192.168.1.1
```

## Compatibility
Linux | Windows | macOS