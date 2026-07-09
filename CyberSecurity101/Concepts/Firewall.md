# Firewall

## Definition
A firewall is a network security device that monitors and controls incoming and outgoing network traffic based on predetermined security rules. Firewalls establish a barrier between trusted internal networks and untrusted external networks (like the Internet). They can be hardware appliances, software running on general-purpose hardware, or cloud-based services.

## Why It Matters
Firewalls are the most fundamental network security control. They are the first line of defense against network-based attacks, blocking unauthorized access, malware communication, and data exfiltration. Properly configured firewalls enforce network segmentation, prevent lateral movement, and protect sensitive systems. Understanding firewall types, rule configuration, and limitations is essential for any security professional.

## Where It Appears in the Path
Firewalls are covered in the network security module. They are prerequisite for understanding network segmentation defense, DMZ architecture, firewall evasion (penetration testing), and integration with IDS/IPS and SIEM systems.

## Prerequisites
- Networking fundamentals (TCP/IP, ports, protocols)
- OSI model (layers 3, 4, 7)

## Firewall Types

### Packet Filter Firewall (Stateless)
Operates at Layer 3-4. Examines individual packets against rules based on source IP, destination IP, source port, destination port, and protocol. No awareness of connection state. Fast but limited. Cannot detect attacks that span multiple packets. Example: iptables (stateless mode), early Cisco ACLs.

### Stateful Firewall
Operates at Layer 3-4. Maintains a "state table" tracking active connections. Makes decisions based on the context of the entire connection, not just individual packets. Automatically allows return traffic for established connections. More secure than stateless. Examples: iptables with conntrack, pfSense, Windows Defender Firewall.

### Application Layer Firewall (Application Gateway/Proxy Firewall)
Operates at Layer 7. Inspects application-layer payload (HTTP requests, DNS queries, FTP commands). Can block specific commands, methods, URLs, or content types. Most advanced and secure but performance-intensive. Examples: mod_security (WAF), AWS WAF, Cloudflare WAF.

### Next-Generation Firewall (NGFW)
Combines stateful inspection with application awareness, intrusion prevention (IPS), SSL/TLS inspection, threat intelligence, and identity awareness. The modern enterprise standard. Examples: Palo Alto Networks, Fortinet FortiGate, Cisco Firepower, Check Point.

### Cloud Firewall (FWaaS)
Firewall-as-a-Service — cloud-hosted firewall that filters traffic for cloud infrastructures. Examples: AWS Security Groups/Network ACLs, Azure Firewall, Google Cloud Armor, Cloudflare Magic Firewall.

## Rule Structure
Firewall rules typically have these components:
1. **Action**: Allow or Deny (the lowest-priority explicit deny is usually implicit at the end)
2. **Source**: IP address, range, subnet, or any
3. **Destination**: IP address, range, subnet, or any
4. **Port/Protocol**: TCP, UDP, ICMP, specific ports (e.g., TCP/443)
5. **Interface**: Ingress/egress direction
6. **Logging**: Whether to log matched traffic
7. **State**: New/Established/Related in stateful firewalls

Best practice: explicit deny rules, least privilege (allow only necessary traffic), order rules from specific to general, document every rule.

## Access Control Lists (ACLs)
ACLs are ordered lists of rules applied to network interfaces. In Cisco IOS, standard ACLs filter by source IP only; extended ACLs filter by source/destination IP, protocol, and port. ACLs on routers are typically stateless. On firewalls/next-gen switches, ACLs are stateful.

## Common Configurations

### Default Deny Policy
All traffic is denied by default — only explicitly allowed traffic passes. Follows the principle of least privilege and zero trust. Recommended for security.

### Default Allow Policy
All traffic is allowed by default — only explicitly denied traffic is blocked. Less secure, easier to manage. Common in internal networks with high trust.

### DMZ (Demilitarized Zone)
A network segment that hosts public-facing services (web, email, DNS). Typically has three interfaces: outside (Internet), inside (internal network), DMZ (public servers). Rules: Internet → DMZ (limited ports), DMZ → Internet (usually allowed), DMZ → Inside (strongly restricted or denied), Inside → DMZ (allowed for management).

## Firewall Evasion Techniques (Penetration Testing)
- **Port Knocking**: Sequence of connection attempts to closed ports triggers rules to open a port.
- **Tunneling**: Encapsulate blocked protocol inside allowed protocol (DNS tunneling, HTTP CONNECT, SSH tunneling).
- **Source Port Manipulation**: Using allowed source ports (e.g., DNS source port 53) to bypass rules.
- **Fragmentation**: Splitting packets so the firewall can't reassemble and inspect.
- **Encoding/Encryption**: Hiding payload content (e.g., base64 encoding in HTTP).
- **IP Address Variation**: Round-robin across many IPs to evade IP-based blocks.

## Common Interview Questions
1. **What is the difference between a stateless and stateful firewall?** Stateless inspects each packet independently based on header fields. Stateful maintains connection state tables and tracks the entire conversation, allowing return traffic automatically.
2. **What is the default security policy of a firewall?** Usually "deny all" (implicit deny) — any traffic not explicitly permitted is blocked. Follows least privilege.
3. **What is a DMZ and why is it used?** A network segment between internal and external networks hosting public-facing services. Limits exposure — if a DMZ server is compromised, the internal network remains protected.
4. **How does an application-layer firewall differ from a packet filter?** Application firewalls inspect Layer 7 content (HTTP headers, SQL queries, file types). Packet filters only inspect Layer 3-4 (IPs and ports).
5. **What is the difference between inbound and outbound firewall rules?** Inbound: traffic coming from outside to inside. Outbound: traffic from inside to outside. Both should be restricted.
6. **How do you test firewall rules for effectiveness?** (1) Review rules against security policy. (2) Use port scanning (nmap) from outside. (3) Verify no unintended access exists. (4) Deploy a test system to validate expected behavior. (5) Check logs for denied/blocked traffic.

## Further Reading
- [NIST SP 800-41 Rev 1 — Guidelines on Firewalls and Firewall Policy](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-41r1.pdf)
- [iptables tutorial](https://www.frozentux.net/iptables-tutorial/)
- [pfSense documentation](https://docs.netgate.com/pfsense/en/latest/)
- [Cisco ASA/FTD Configuration Guide](https://www.cisco.com/c/en/us/support/security/asa-firepower-services/products-installation-and-configuration-guides-list.html)
- [OWASP Firewall Evasion](https://owasp.org/www-community/attacks/Firewall_Evasion)
