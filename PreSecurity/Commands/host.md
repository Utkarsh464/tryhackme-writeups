# host

## Syntax
`host [options] domain [server]`

## Purpose
Simple DNS lookup utility that resolves hostnames to IP addresses and vice versa.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-t TYPE` | Query specific record type |
| `-a` | Show all records |
| `-l` | Zone transfer (if allowed) |
| `-v` | Verbose output |

## Examples
```bash
host example.com
host -t MX example.com
host 1.1.1.1
```

## Compatibility
Linux | macOS