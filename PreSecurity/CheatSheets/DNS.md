# DNS Cheat Sheet

## Record Types
| Record | Purpose | Example |
|--------|---------|---------|
| A | IPv4 address mapping | `example.com → 93.184.216.34` |
| AAAA | IPv6 address mapping | `example.com → 2606:2800:220:1:248:1893:25c8:1946` |
| CNAME | Canonical name (alias) | `www.example.com → example.com` |
| MX | Mail exchange server | `example.com → mail.example.com (priority 10)` |
| TXT | Arbitrary text (SPF, DKIM, DMARC) | `v=spf1 include:_spf.google.com` |
| NS | Authoritative nameserver | `example.com → ns1.example.com` |
| PTR | Reverse DNS (IP → domain) | `34.216.184.93 → example.com` |
| SOA | Start of Authority (zone metadata) | Admin email, serial, refresh, retry, expiry |
| SRV | Service location (SIP, LDAP) | `_sip._tcp.example.com → priority weight port host` |

## Lookup Commands
| Command | Description |
|---------|-------------|
| `dig example.com ANY` | All records |
| `dig example.com MX +short` | MX only, brief |
| `dig -x 8.8.8.8` | Reverse lookup |
| `dig @1.1.1.1 example.com` | Use custom resolver |
| `nslookup example.com` | Basic lookup |
| `nslookup -type=MX example.com` | Query specific type |
| `host example.com` | Simple lookup |
| `host -t AAAA example.com` | AAAA record |
| `whois example.com` | Registration info |

## DNS Resolution Steps
1. Client checks local DNS cache
2. Queries recursive resolver (ISP/public DNS)
3. Resolver queries root servers → TLD servers → authoritative servers
4. Authoritative server returns the record
5. Result cached based on TTL

## Common DNS Attacks
| Attack | Description |
|--------|-------------|
| DNS Spoofing / Cache Poisoning | Attacker injects false DNS records |
| DNS Tunneling | Encapsulate data in DNS queries for C2/exfil |
| DNS Amplification | Small queries generate large responses (DDoS) |
| Zone Transfer (AXFR) | Unauthorized retrieval of entire DNS zone |
| DNS Rebinding | Attacker-controlled domain resolves to internal IP |