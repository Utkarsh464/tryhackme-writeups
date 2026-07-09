# DNS

## Definition
The Domain Name System (DNS) is the Internet's phonebook — it translates human-readable domain names (like `tryhackme.com`) into machine-readable IP addresses (like `104.18.25.114`). DNS is a hierarchical, distributed database that maps domain names to various types of resource records. It operates on UDP port 53 (primary) and TCP port 53 (zone transfers, large responses).

## Why It Matters
DNS is critical infrastructure — without it, users would have to memorize IP addresses for every website. In cybersecurity, DNS is both an attack vector and a detection mechanism. Attackers exploit DNS for command-and-control (C2) communication, data exfiltration (DNS tunneling), phishing (typosquatting), and denial of service. Defenders analyze DNS logs to detect malware infections, data exfiltration, and malicious domains.

## Where It Appears in the Path
DNS is introduced in the networking module. It is prerequisite knowledge for HTTP/HTTPS (web browsing uses DNS), web security, phishing attacks, and network forensics. DNS attacks are covered in threat intelligence and penetration testing modules.

## Prerequisites
- Basic networking (IP addresses, ports)
- Understanding client-server model

## DNS Record Types
- **A (Address)**: Maps a domain name to an IPv4 address.
- **AAAA (Quad A)**: Maps a domain name to an IPv6 address.
- **CNAME (Canonical Name)**: Alias — maps one domain to another (e.g., `www.example.com` → `example.com`).
- **MX (Mail Exchange)**: Specifies email servers for a domain with priority values.
- **NS (Name Server)**: Delegates DNS zones to authoritative name servers.
- **TXT (Text)**: Arbitrary text data — used for SPF, DKIM, DMARC email authentication, and domain ownership verification.
- **SOA (Start of Authority)**: Contains administrative info about the zone (primary NS, admin email, serial number, refresh/retry/expiry TTLs).
- **SRV (Service)**: Specifies services (like SIP, LDAP) with host and port.
- **PTR (Pointer)**: Reverse DNS — maps IP addresses to hostnames (used in rDNS lookups).

## DNS Resolution Process
1. **User enters URL** in browser — OS checks local DNS cache.
2. **Stub resolver** (in the OS) forwards query to the configured recursive resolver (usually ISP or public DNS like 8.8.8.8).
3. **Recursive resolver** (root hints → TLD → authoritative) performs iterative queries:
   - Query root server: "Who manages .com?"
   - Query .com TLD server: "Who manages example.com?"
   - Query example.com authoritative server: "What is the IP of www.example.com?"
4. **Response** returned to the resolver, cached with a TTL.
5. **Resolver** returns IP to the stub resolver → OS → browser.

## DNS Attacks

### DNS Spoofing / Cache Poisoning
An attacker injects forged DNS records into a recursive resolver's cache, redirecting users to malicious sites. Mitigations: DNSSEC (DNS Security Extensions) validates DNS responses with digital signatures.

### DNS Tunneling
Encodes data (C2 commands, exfiltrated files) within DNS query and response packets. Hard to block because DNS is normally allowed through firewalls. Detection: monitoring unusual DNS query volumes, long subdomains, TXT record payloads.

### DDoS Amplification
Attacker sends DNS queries with a spoofed source IP (the victim). DNS server responds with a larger response to the victim, amplifying traffic up to 50-100x. Mitigations: disable open recursion, rate limiting, BCP 38 (anti-spoofing).

### Typosquatting & Domain Hijacking
Attackers register similar domain names (`g00gle.com`) to capture traffic, or compromise domain registrars to redirect legitimate domains.

## Common Interview Questions
1. **What happens when you type a URL into a browser (DNS part)?** The browser checks local cache → `/etc/hosts` file → queries the configured DNS resolver → which performs iterative/recursive queries → returns IP → browser opens TCP connection.
2. **What is the difference between recursive and iterative DNS queries?** Recursive: the resolver handles all queries and returns a complete answer. Iterative: the resolver queries servers one by one, each providing a referral to the next.
3. **What is DNSSEC and how does it work?** DNSSEC adds cryptographic signatures to DNS records, enabling resolvers to verify authenticity. Uses RRSIG, DNSKEY, DS, and NSEC records to create a chain of trust.
4. **What are common DNS attack types?** Cache poisoning, DNS tunneling, DDoS amplification, typo squatting, domain hijacking, NXDOMAIN attacks, random subdomain attacks.
5. **What is the difference between authoritative and recursive DNS?** Authoritative holds the actual zone records; recursive resolves queries on behalf of clients by traversing the DNS hierarchy.
6. **How can DNS logs be used in incident response?** Identify infected clients (querying C2 domains), detect data exfiltration (DNS tunneling), identify compromised domains, track infection spread.

## Further Reading
- [RFC 1034 — Domain Names Concepts and Facilities](https://tools.ietf.org/html/rfc1034)
- [RFC 1035 — Domain Names Implementation and Specification](https://tools.ietf.org/html/rfc1035)
- [DNS Security: DNSSEC](https://www.cloudflare.com/dns/dnssec/how-dnssec-works/)
- [OWASP DNS Tunneling](https://owasp.org/www-community/attacks/DNS_Tunneling)
- `dig`, `nslookup`, `host` command line tools practice
