# dig

## Syntax
`dig [@server] domain [record-type] [options]`

## Purpose
DNS lookup utility that queries DNS servers and returns detailed record information (more flexible than nslookup).

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `@server` | DNS server to query (e.g., `@8.8.8.8`) |
| `+short` | Brief output (IP only) |
| `+noall +answer` | Show only answer section |
| `-x` | Reverse DNS lookup |

## Examples
```bash
dig example.com
dig example.com MX +short
dig -x 1.1.1.1
dig @8.8.8.8 tryhackme.com
```

## Compatibility
Linux | macOS