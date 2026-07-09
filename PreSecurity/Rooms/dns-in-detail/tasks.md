# Tasks: DNS in Detail

## Task 1: DNS Hierarchy
**Purpose:** Understand the hierarchical structure of DNS.

**Skills:** Domain name system fundamentals.

**Theory:** DNS has a tree-like hierarchy: the root (`.`), Top-Level Domains like `.com`, `.org`, `.uk` (TLDs), Second-Level Domains like `google` (SLDs), and subdomains like `www` or `mail`. Each level is managed by a different authority, from ICANN (root) to registrars (SLDs).

**Commands:** N/A

---

## Task 2: Record Types
**Purpose:** Learn about DNS record types.

**Skills:** DNS resource records.

**Theory:** A records map a domain to an IPv4 address. AAAA records map to IPv6. CNAME records alias one domain to another. MX records specify mail servers with priority values. TXT records store arbitrary text (often used for verification). NS records indicate authoritative name servers.

**Commands:** `dig google.com A`, `dig google.com MX`

---

## Task 3: DNS Resolution Process
**Purpose:** Understand how DNS queries are resolved.

**Skills:** Recursive and authoritative resolution.

**Theory:** A recursive DNS resolver queries the root server, then the TLD server, then the authoritative name server on behalf of the client. Authoritative servers hold the actual DNS records for a domain. Results are cached to speed up subsequent queries.

**Commands:** `dig +trace google.com`

---

## Task 4: DNS Attacks
**Purpose:** Recognize common DNS attack vectors.

**Skills:** DNS security awareness.

**Theory:** DNS spoofing (cache poisoning) injects false DNS records into a resolver's cache. DNS tunnelling encodes non-DNS traffic (like SSH or HTTP) inside DNS queries to bypass firewalls. DDoS attacks often amplify DNS traffic using open resolvers.

**Commands:** N/A

---
