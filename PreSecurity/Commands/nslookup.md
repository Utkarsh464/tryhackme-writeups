# nslookup

## Syntax
`nslookup [options] [domain] [server]`

## Purpose
Queries DNS servers to resolve domain names to IP addresses and retrieve DNS records.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-type=TYPE` | Query specific record type (A, MX, TXT, etc.) |
| `-debug` | Show full query details |
| `server` | Specify DNS server to query (second argument) |

## Examples
```bash
nslookup example.com
nslookup -type=MX example.com
nslookup example.com 8.8.8.8
```

## Compatibility
Linux | Windows | macOS