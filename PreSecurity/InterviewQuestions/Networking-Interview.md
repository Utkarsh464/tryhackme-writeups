# Networking Interview Questions

## 1. Explain the OSI model and its seven layers.
**Answer:** The OSI (Open Systems Interconnection) model is a conceptual framework with seven layers: Physical (cables, bits), Data Link (frames, MAC addresses, switches), Network (packets, IP addresses, routers), Transport (segments, TCP/UDP, port numbers), Session (establishes/manages connections), Presentation (encryption, encoding, compression), and Application (HTTP, FTP, DNS, SMTP). Each layer provides services to the layer above and receives services from the layer below.

## 2. What is the TCP/IP model and how does it differ from OSI?
**Answer:** The TCP/IP model is a practical four-layer framework: Network Access (combines OSI 1-2, handles physical transmission), Internet (OSI 3, IP addressing and routing), Transport (OSI 4, TCP/UDP reliability and flow control), and Application (OSI 5-7, application protocols). It is less rigid than OSI and reflects how the internet actually functions, with fewer layers and more flexibility.

## 3. What is the difference between TCP and UDP?
**Answer:** TCP (Transmission Control Protocol) is connection-oriented, providing reliable delivery through sequencing, acknowledgments, retransmission, and flow control — ideal for web browsing, email, and file transfer. UDP (User Datagram Protocol) is connectionless, offering faster but unreliable delivery with no guarantees — ideal for streaming, VoIP, DNS lookups, and online gaming where speed matters more than perfect reliability.

## 4. How does DNS resolution work?
**Answer:** DNS resolution converts domain names to IP addresses. The client queries a recursive resolver, which checks its cache. If not found, it queries root nameservers (directing to TLD servers), TLD nameservers (directing to authoritative servers), and finally the authoritative nameserver returns the IP address. The result is cached and returned to the client. The process typically takes milliseconds.

## 5. What is the difference between HTTP and HTTPS?
**Answer:** HTTP transmits data in plaintext, making it vulnerable to interception and modification (man-in-the-middle attacks). HTTPS uses TLS (Transport Layer Security) to encrypt all communication between client and server, ensuring confidentiality, integrity, and authentication via digital certificates. HTTPS uses port 443 by default; HTTP uses port 80.

## 6. What are common ports and their associated protocols?
**Answer:** Common ports include: 20/21 (FTP), 22 (SSH), 23 (Telnet), 25 (SMTP), 53 (DNS), 80 (HTTP), 110 (POP3), 143 (IMAP), 443 (HTTPS), 3389 (RDP), 3306 (MySQL), 5432 (PostgreSQL), 27017 (MongoDB), 161 (SNMP), 389 (LDAP), 636 (LDAPS). Knowing these is essential for firewall configuration, network troubleshooting, and security assessments.

## 7. Explain subnetting and CIDR notation.
**Answer:** Subnetting divides a larger network into smaller, manageable subnetworks by borrowing host bits for network prefixes. CIDR (Classless Inter-Domain Routing) notation specifies the network prefix length, e.g., 192.168.1.0/24 means the first 24 bits are the network portion. Subnetting improves IP address efficiency, reduces broadcast domains, and enhances security through network segmentation.

## 8. What is ARP and how does it work?
**Answer:** ARP (Address Resolution Protocol) maps IP addresses to MAC addresses on a local network. When a device needs to communicate with another IP on the same subnet, it broadcasts an ARP request: "Who has IP X?" The device with that IP responds with its MAC address. The mapping is cached in the ARP table to avoid repeated broadcasts. ARP spoofing is a common attack vector.

## 9. Describe the TCP three-way handshake.
**Answer:** The three-way handshake establishes a TCP connection: Step 1 — Client sends a SYN packet with a random sequence number (SEQ=x). Step 2 — Server responds with SYN-ACK, acknowledging the client's SEQ (ACK=x+1) and sending its own sequence number (SEQ=y). Step 3 — Client sends ACK acknowledging the server's sequence number (ACK=y+1). The connection is then established and data transfer begins.

## 10. What are the differences between a switch, a router, and a hub?
**Answer:** A hub operates at Layer 1, broadcasting all data to all ports with no intelligence. A switch operates at Layer 2, using MAC addresses to forward frames only to the correct port, reducing collisions. A router operates at Layer 3, using IP addresses to route packets between different networks, and typically includes NAT, firewall, and DHCP capabilities. Switches connect devices within a network; routers connect networks.

## 11. What is NAT and why is it used?
**Answer:** NAT (Network Address Translation) maps private IP addresses (e.g., 192.168.x.x, 10.x.x.x) to a public IP address for internet communication. It conserves IPv4 address space, provides a basic layer of security by hiding internal IP structures, and allows multiple devices to share a single public IP. Types include Static NAT (one-to-one mapping), Dynamic NAT (pool of public IPs), and PAT (port address translation, many-to-one).

## 12. How does DHCP work?
**Answer:** DHCP (Dynamic Host Configuration Protocol) automates IP address assignment. The process (DORA): Discover — client broadcasts a DHCP discovery message. Offer — DHCP server offers an IP address and configuration. Request — client requests the offered address. Acknowledge — server acknowledges and assigns the lease. DHCP also provides subnet mask, default gateway, DNS servers, and lease duration.

## 13. What are the common HTTP methods?
**Answer:** The most common HTTP methods are: GET (retrieve a resource), POST (submit data to create a resource), PUT (update/replace a resource), PATCH (partial update), DELETE (remove a resource), HEAD (same as GET but returns headers only), OPTIONS (describe available methods), and CONNECT (establish a tunnel, used for HTTPS). Safe methods (GET, HEAD) shouldn't change server state; idempotent methods (PUT, DELETE) produce the same result on repeated calls.

## 14. What are common HTTP status codes?
**Answer:** Status codes are grouped: 1xx (Informational — 100 Continue, 101 Switching Protocols), 2xx (Success — 200 OK, 201 Created, 204 No Content), 3xx (Redirection — 301 Moved Permanently, 302 Found, 304 Not Modified), 4xx (Client Error — 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 405 Method Not Allowed, 429 Too Many Requests), 5xx (Server Error — 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable).

## 15. What is a VPN and how does it work?
**Answer:** A VPN (Virtual Private Network) creates an encrypted tunnel between a client and a VPN server, protecting data in transit and masking the client's IP address. It uses tunneling protocols (OpenVPN, WireGuard, IPSec) to encapsulate and encrypt traffic. VPNs are used for remote access to corporate networks, bypassing geo-restrictions, and securing communication on untrusted networks like public Wi-Fi.

## 16. What is a VLAN and why is it used?
**Answer:** A VLAN (Virtual Local Area Network) logically segments a physical network into separate broadcast domains without requiring physical separation. VLANs improve security (isolating sensitive systems), reduce broadcast traffic, simplify network management, and allow devices in different physical locations to belong to the same network segment. VLAN tagging (802.1Q) identifies which VLAN a frame belongs to.
