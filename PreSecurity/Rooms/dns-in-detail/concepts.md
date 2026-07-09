# Concepts: DNS in Detail

## 1. DNS Hierarchy
DNS is organized as an inverted tree. The root zone (`.`) is at the top, managed by 13 root server clusters. Below are TLDs (`.com`, `.org`, `.net`, country codes). Below those are SLDs (`example.com`). Subdomains (`blog.example.com`) branch off SLDs. Each level delegates authority to the next.

## 2. Top-Level Domains (TLDs)
TLDs are the highest level of the DNS hierarchy after the root. They include generic TLDs (gTLDs) like `.com`, `.org`, `.net`, sponsored TLDs (sTLDs) like `.gov`, `.edu`, and country-code TLDs (ccTLDs) like `.uk`, `.de`, `.jp`.

## 3. A Record
An A (Address) record maps a domain name to a 32-bit IPv4 address. This is the most fundamental DNS record type — without it, a domain cannot be reached by IPv4 clients. Multiple A records can exist for load balancing.

## 4. CNAME Record
A CNAME (Canonical Name) record maps one domain name to another. For example, `www.example.com` might be a CNAME pointing to `example.com`. CNAMEs cannot coexist with other record types for the same name and cannot point to IP addresses.

## 5. MX Record
MX (Mail Exchange) records specify mail servers for a domain. Each MX record has a priority number: lower numbers are preferred. If the highest-priority server is unreachable, the next priority server is used.

## 6. Recursive DNS Query
In a recursive query, the DNS resolver handles the full resolution process: it queries the root, then the TLD, then the authoritative server, and returns the final answer to the client. The client only makes one request to the resolver.

## 7. Authoritative DNS Server
An authoritative DNS server holds the official DNS records for a domain. When a recursive resolver queries an authoritative server, it receives the definitive answer. Authoritative servers do not cache — they respond with their own configured records.

## 8. DNS Spoofing / Cache Poisoning
An attack where an attacker injects forged DNS records into a resolver's cache. When users query the poisoned domain, they are directed to a malicious IP address instead of the legitimate one, enabling phishing, malware distribution, or man-in-the-middle attacks.
