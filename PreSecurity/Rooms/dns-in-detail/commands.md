# Commands: DNS in Detail

## Query Tools

| Command | Description |
|---------|-------------|
| `dig google.com` | General DNS lookup for a domain |
| `dig google.com A` | Query A records for a domain |
| `dig google.com AAAA` | Query AAAA (IPv6) records |
| `dig google.com MX` | Query mail exchange records |
| `dig google.com TXT` | Query TXT records |
| `dig google.com NS` | Query authoritative name servers |
| `dig +trace google.com` | Show the full recursive resolution path |
| `nslookup google.com` | Simple DNS lookup (older tool) |
| `nslookup -type=MX google.com` | Query specific record type with nslookup |

## Name Resolution

| Command | Description |
|---------|-------------|
| `host google.com` | Simplified DNS lookup |
| `cat /etc/resolv.conf` | View configured DNS servers |
| `systemd-resolve --status` | View system DNS configuration |
