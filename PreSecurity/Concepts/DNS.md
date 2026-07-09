# DNS

## Definition
The Domain Name System (DNS) translates human-readable domain names (e.g., example.com) into IP addresses. It is a hierarchical, distributed database with root servers, TLD servers, and authoritative nameservers. Record types include A (IPv4), AAAA (IPv6), MX (mail), CNAME (alias), and TXT (text).

## Why It Matters
DNS is critical to internet functionality and a frequent attack vector. Threats include DNS spoofing/cache poisoning, DNS tunneling (exfiltration), and DDoS amplification. Security tools like dnscat2 and techniques like DNS sinkholing all rely on understanding DNS resolution.

## Where It Appears in the Path
- How The Web Works
- DNS in Detail

## Prerequisites
- Networking basics, IP addressing

## Key Points
- Recursive resolution: client → resolver → root → TLD → authoritative
- TTL (Time To Live) controls caching duration
- DNS queries use UDP port 53; zone transfers use TCP 53
- Dynamic DNS allows hostnames to update automatically

## Common Interview Questions
1. What is the difference between recursive and iterative DNS queries?
**Answer:** In recursive, the resolver does all the work; in iterative, the resolver follows referrals.
2. What is DNS poisoning?
**Answer:** Corrupting a DNS cache with false records to redirect traffic.

## Further Reading
- RFC 1034, RFC 1035
- OWASP DNS Recon