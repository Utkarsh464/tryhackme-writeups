# Networking Interview Questions & Answers

## 1. Explain the OSI model and its 7 layers.

**Answer:** The OSI (Open Systems Interconnection) model standardizes network communication into 7 layers: Layer 7 - Application (HTTP, FTP, DNS - user-facing protocols); Layer 6 - Presentation (encryption, compression, data formatting like SSL/TLS); Layer 5 - Session (establishes/manages/terminates sessions - NetBIOS, RPC); Layer 4 - Transport (TCP/UDP, segmentation, reliability, flow control); Layer 3 - Network (IP, routing, logical addressing - routers); Layer 2 - Data Link (Ethernet, MAC addresses, frames, switches); Layer 1 - Physical (cables, signals, bits, hubs). Data flows down the stack at sender (encapsulation with headers) and up at receiver (decapsulation). The mnemonic is "Please Do Not Throw Sausage Pizza Away".

## 2. Explain the TCP/IP model vs OSI model.

**Answer:** The TCP/IP model has 4 layers: Application (combines OSI L5-7 - HTTP, FTP, SMTP, DNS, SSH), Transport (TCP, UDP), Internet (equivalent to OSI L3 - IP, ICMP, ARP), Network Access (combines OSI L1-2 - Ethernet, WiFi, PPP). TCP/IP is the practical implementation; OSI is a conceptual reference. TCP/IP was developed by DoD, focuses on reliability and interconnection. Key difference: OSI separates presentation/session layers; TCP/IP doesn't. TCP/IP protocols were developed alongside the model; OSI was designed first, protocols later (largely unsuccessful).

## 3. Explain TCP vs UDP differences and use cases.

**Answer:** TCP (Transmission Control Protocol): Connection-oriented, reliable, ordered delivery, error checking, flow control, congestion control, retransmission of lost packets. 3-way handshake (SYN, SYN-ACK, ACK). Higher overhead. Use cases: HTTP/HTTPS, FTP, SSH, SMTP, DNS (zone transfers). UDP (User Datagram Protocol): Connectionless, unreliable, no ordering guarantee, no retransmission, no flow/congestion control. Lower overhead, lower latency. Use cases: DNS queries, DHCP, VoIP, video streaming, gaming, SNMP, NTP, TFTP. TCP header: 20-60 bytes; UDP header: 8 bytes.

## 4. How does DNS resolution work?

**Answer:** DNS resolves domain names to IP addresses. Process: 1) User types example.com in browser. 2) Browser checks local cache. 3) OS checks hosts file (/etc/hosts). 4) Query goes to recursive resolver (usually ISP or Cloudflare 1.1.1.1). 5) Resolver queries root name servers (., 13 root servers). 6) Root responds with TLD server (.com). 7) Resolver queries TLD server for authoritative nameserver. 8) Authoritative server returns A/AAAA record (IP). 9) Resolver caches result and returns to client. Record types: A (IPv4), AAAA (IPv6), CNAME (alias), MX (mail), NS (nameserver), TXT (text, SPF, DKIM), PTR (reverse).

## 5. What is the difference between HTTP and HTTPS?

**Answer:** HTTPS is HTTP over TLS/SSL (port 443 vs 80). HTTPS provides: 1) Encryption - data is encrypted with symmetric session key (prevents eavesdropping). 2) Authentication - server identity verified via digital certificate from CA (prevents MITM). 3) Integrity - MAC ensures data isn't modified in transit. TLS handshake: Client Hello, Server Hello + Certificate, Key Exchange, Finished. HTTPS uses asymmetric crypto for key exchange, symmetric for data. Certificate types: DV (domain validated), OV (organization), EV (extended validation). HTTP/2 and HTTP/3 (QUIC) require HTTPS.

## 6. Explain common ports and their associated protocols.

**Answer:** 20/21 - FTP (data/control), 22 - SSH, 23 - Telnet (unencrypted), 25 - SMTP (email sending), 53 - DNS (both TCP/UDP), 67/68 - DHCP, 80 - HTTP, 110 - POP3 (email retrieval), 123 - NTP, 143 - IMAP (email retrieval), 161/162 - SNMP, 389 - LDAP, 443 - HTTPS, 445 - SMB (Windows file sharing), 465 - SMTPS, 514 - Syslog, 587 - SMTP submission, 636 - LDAPS, 993 - IMAPS, 995 - POP3S, 1433 - MSSQL, 1521 - Oracle DB, 2049 - NFS, 3306 - MySQL, 3389 - RDP, 5432 - PostgreSQL, 5900 - VNC, 6379 - Redis, 8080 - HTTP alternate, 8443 - HTTPS alternate, 27017 - MongoDB.

## 7. Explain subnetting and CIDR notation.

**Answer:** Subnetting divides a network into smaller subnetworks. CIDR (Classless Inter-Domain Routing) notation: `192.168.1.0/24` - the /24 means 24 bits are network, 8 bits are hosts. The subnet mask (255.255.255.0) defines the boundary. Key formula: Number of hosts = 2^(32 - prefix) - 2 (one for network, one for broadcast). Examples: /24 = 254 hosts, /16 = 65,534 hosts, /30 = 2 hosts (point-to-point), /32 = 1 host. VLSM (Variable Length Subnet Mask) allows different subnet sizes. Calculation: AND IP with subnet mask to get network address. Private ranges: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16.

## 8. How does ARP work?

**Answer:** ARP (Address Resolution Protocol) resolves IP addresses to MAC addresses on a local network. Process: 1) Host A wants to send to IP 192.168.1.5. 2) A checks its ARP cache (`arp -a`). 3) If not cached, A broadcasts an ARP request: "Who has 192.168.1.5? Tell 192.168.1.10". 4) All hosts on the LAN receive the broadcast; only host B with that IP responds. 5) B sends ARP reply (unicast) with its MAC address. 6) A caches the mapping and sends the frame. ARP spoofing/poisoning is a MITM attack where an attacker sends forged ARP replies to associate their MAC with another IP.

## 9. Explain the 3-way handshake and TCP connection termination.

**Answer:** 3-way handshake establishes TCP connection: 1) Client sends SYN (seq=x) to server. 2) Server responds with SYN-ACK (seq=y, ack=x+1). 3) Client sends ACK (ack=y+1). Connection is now ESTABLISHED. SYN flag synchronizes sequence numbers. Termination (4-way): 1) Client sends FIN. 2) Server sends ACK, then FIN. 3) Client sends ACK. TIME_WAIT state ensures remaining packets are processed. States: LISTEN, SYN-SENT, SYN-RECEIVED, ESTABLISHED, FIN-WAIT-1/2, CLOSE-WAIT, LAST-ACK, TIME-WAIT, CLOSED. Attackers use SYN floods (send SYNs without completing handshake) for DoS.

## 10. What is the difference between a switch, router, and hub?

**Answer:** Hub (Layer 1): Broadcasts data to all ports, no intelligence, half-duplex, collision-prone, obsolete for Ethernet. Switch (Layer 2): Forwards frames based on MAC address table, full-duplex, creates separate collision domains, learns MAC addresses dynamically (CAM table). Router (Layer 3): Forwards packets based on IP addresses, connects different networks, maintains routing tables, performs NAT, has firewall capabilities. Switches are for LAN segmentation; routers connect LANs to WAN/internet. Multilayer switches combine L2 switching with L3 routing.

## 11. Explain NAT and its types.

**Answer:** NAT (Network Address Translation) maps private IPs to public IPs for internet access. Types: 1) SNAT (Source NAT) - changes source IP of outgoing packets (masquerading). 2) DNAT (Destination NAT) - changes destination IP of incoming packets (port forwarding). 3) 1:1 NAT - maps one private IP to one public IP. 4) PAT (Port Address Translation) - many private IPs to one public IP using different ports (most common in home routers). Advantages: conserves IPv4 addresses, hides internal network, allows IP overlap. Disadvantages: breaks end-to-end principle, complicates some protocols (FTP, SIP need ALG).

## 12. How does DHCP work?

**Answer:** DHCP (Dynamic Host Configuration Protocol) assigns IP addresses automatically. DORA process: 1) DISCOVER - Client broadcasts "I need an IP". 2) OFFER - DHCP server responds with offered IP, subnet mask, gateway, DNS. 3) REQUEST - Client requests the offered IP. 4) ACK - Server acknowledges and assigns the IP. Lease times determine how long the IP is valid (renewal at 50%, rebind at 87.5%). DHCP relay forwards broadcasts across subnets. Static DHCP (reservation) assigns fixed IP based on MAC. Rogue DHCP servers can cause MITM attacks.

## 13. Explain the common HTTP methods and status codes.

**Answer:** Methods: GET (retrieve resource), POST (submit data), PUT (replace resource), PATCH (partial update), DELETE (remove resource), HEAD (GET without body), OPTIONS (what methods are supported), CONNECT (tunnel, used for HTTPS proxy), TRACE (diagnostic echo). Status codes: 1xx (Informational) - 100 Continue, 101 Switching Protocols. 2xx (Success) - 200 OK, 201 Created, 204 No Content. 3xx (Redirection) - 301 Moved Permanently, 302 Found, 304 Not Modified. 4xx (Client Error) - 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 405 Method Not Allowed, 429 Too Many Requests. 5xx (Server Error) - 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable, 504 Gateway Timeout.

## 14. What is a VPN and how does it work?

**Answer:** A VPN (Virtual Private Network) creates an encrypted tunnel between client and server, securing traffic over untrusted networks. Protocols: OpenVPN (open source, UDP/TCP, highly configurable), WireGuard (modern, simpler, faster, in-kernel), IPsec (IKEv1/IKEv2, works in transport or tunnel mode), PPTP (obsolete, insecure). VPN tunneling encapsulates packets: original packet is encrypted and wrapped with new header for routing. Use cases: remote access (employee to corporate network), site-to-site (branch to HQ), privacy/geobypass. Split tunneling routes some traffic through VPN, some direct.

## 15. Explain packet flow through a network.

**Answer:** 1) Application generates data, passes to transport layer. 2) Transport adds TCP/UDP header (port numbers), creates segment. 3) Network layer adds IP header (source/dest IPs), creates packet. 4) Data link adds Ethernet header (source/dest MACs + type), trailer (FCS for error detection), creates frame. 5) Physical layer sends bits as electrical/optical signals. 6) Router receives, strips L2 header, checks routing table, rewrites L2 header, forwards. 7) Destination receives, performs reverse decapsulation up the stack. Each router decrements TTL. MTU determines max packet size; fragmentation occurs if exceeded.

## 16. What is the difference between IDS and IPS?

**Answer:** IDS (Intrusion Detection System): Passive monitoring, analyzes traffic and alerts on suspicious activity, no inline blocking, cannot stop attacks in real-time. IPS (Intrusion Prevention System): Inline, actively blocks malicious traffic, can drop/reject packets, sits in the traffic path. Types: Network-based (NIDS/NIPS - monitors network traffic), Host-based (HIDS/HIPS - monitors system logs/processes). Detection methods: Signature-based (matches known patterns - low false positives, misses zero-days), Anomaly-based (behavioral baselines - detects novel attacks, higher false positives), Stateful protocol analysis.

## 17. Explain the concept of VLANs.

**Answer:** A VLAN (Virtual LAN) segments a physical network into multiple logical networks. VLANs isolate traffic at Layer 2, reducing broadcast domains and improving security. Switches tag frames with 802.1Q VLAN tag (4 bytes, 12-bit VLAN ID = up to 4096 VLANs). Trunk ports carry multiple VLANs between switches. Access ports assign a single VLAN to connected devices. VLAN hopping attacks exploit default VLAN 1 or double-tagging. Benefits: network segmentation without extra hardware, improved performance (fewer broadcasts), easier management, compliance isolation.

## 18. How does load balancing work?

**Answer:** Load balancing distributes traffic across multiple servers for availability and performance. Types: Layer 4 (transport-level, based on IP/port, faster), Layer 7 (application-level, inspects HTTP headers/cookies, smarter routing). Algorithms: Round Robin (sequential), Least Connections (to server with fewest active connections), IP Hash (client always goes to same server for session persistence), Weighted (based on server capacity), Random. Features: Health checks (active/passive), SSL termination, session persistence (sticky sessions), DDoS protection. HAProxy, Nginx, F5, AWS ELB are common load balancers.

## 19. Explain wireless networking security protocols.

**Answer:** WEP (Wired Equivalent Privacy): obsolete, uses RC4 with 24-bit IV, cracked in minutes. WPA (Wi-Fi Protected Access): TKIP encryption, improved over WEP but still vulnerable. WPA2 (IEEE 802.11i): AES-CCMP encryption, mandatory for Wi-Fi since 2006. WPA3: SAE (Simultaneous Authentication of Equals) replaces Pre-Shared Key, forward secrecy, protects against dictionary attacks. Enterprise mode uses 802.1X/RADIUS for individual authentication. EAP types: PEAP, EAP-TLS, EAP-TTLS. Attacks: WPS PIN brute force, KRACK (key reinstallation attack), Evil Twin, Deauth attacks.

## 20. What is BGP and how does internet routing work?

**Answer:** BGP (Border Gateway Protocol) is the routing protocol of the internet. Autonomous Systems (AS) use BGP to exchange routing information. eBGP runs between ASes, iBGP within an AS. BGP is a path-vector protocol using attributes like AS_PATH, NEXT_HOP, LOCAL_PREF, MED for route selection. Internet routing: tier 1 ISPs (global backbone), tier 2 (regional, peer with tier 1), tier 3 (retail ISPs). BGP hijacking occurs when an AS advertises prefixes it doesn't own. Route leaks cause traffic to take unintended paths. RPKI (Resource Public Key Infrastructure) secures BGP with route origin validation.

## 21. Explain network troubleshooting methodology.

**Answer:** Systematic troubleshooting using the OSI model: 1) Physical - check cables, link lights, interface status (`ip link`). 2) Data Link - check MAC addresses, ARP cache, switch ports. 3) Network - ping gateway, check routing table (`ip route`), traceroute to target, verify IP config. 4) Transport - check port reachability (`nc -zv`, `telnet`), verify firewall rules. 5) Application - test with curl/wget, check service status, examine logs. Common tools: `ping`, `traceroute`, `nslookup`, `dig`, `curl`, `nc`, `tcpdump`, `wireshark`, `ss`, `ip`, `nmap`, `mtr` (combines ping + traceroute).

## 22. What are the differences between symmetric and asymmetric encryption in networking?

**Answer:** Symmetric encryption uses the same key for encryption and decryption. Fast and efficient for bulk data. Algorithms: AES (128/256-bit), ChaCha20, 3DES (obsolete). Key exchange is the challenge. Asymmetric encryption uses public/private key pairs. Slower, used for key exchange, digital signatures. Algorithms: RSA (2048/4096-bit), ECC (ECDH, ECDSA), Diffie-Hellman. In practice: TLS uses asymmetric encryption for initial handshake (key exchange) and authentication via certificates, then switches to symmetric encryption for bulk data transfer. This hybrid approach combines security with performance.

## 23. Explain how a firewall works and types.

**Answer:** Firewalls filter traffic based on rules. Types: 1) Packet filter (stateless) - examines headers (IP, port, protocol), no connection tracking, fast but limited. 2) Stateful - tracks connection state (ESTABLISHED, RELATED, NEW), allows return traffic automatically. 3) Application/Proxy - inspects application data, terminates connections, provides deep packet inspection (DPI). 4) Next-Gen (NGFW) - combines firewall with IPS, application awareness, identity-based policies. 5) Web Application Firewall (WAF) - protects web apps from L7 attacks (SQLi, XSS). Linux: iptables/nftables. Windows: Windows Defender Firewall. Cloud: Security Groups, NACLs.

## 24. What is SDN (Software-Defined Networking)?

**Answer:** SDN separates the control plane (decision-making) from the data plane (forwarding). The control plane runs on a centralized controller (e.g., OpenDaylight, ONOS) that programs switches via protocols like OpenFlow. Benefits: centralized management, programmability, dynamic configuration, easier network automation, improved resource utilization. SDN enables network virtualization, traffic engineering, and automated responses. Challenges: scalability, single point of failure, security of controller. Related: NFV (Network Function Virtualization) virtualizes network appliances (firewalls, load balancers) as software.

## 25. Explain the concept of MTU and fragmentation.

**Answer:** MTU (Maximum Transmission Unit) is the largest packet size a link can transmit. Standard Ethernet MTU is 1500 bytes. If a packet exceeds the MTU, it must be fragmented (IPv4) or the sender must use Path MTU Discovery. Fragmentation splits the IP packet into smaller fragments, each with its own header. Fragments are reassembled at the destination. Problems: fragmentation increases overhead, fragments can be used for evasion (fragmentation attacks, Tiny Fragment attack), and some firewalls can't inspect fragments properly. IPv6 handles fragmentation differently (only source can fragment, uses Path MTU Discovery with ICMPv6). Jumbo frames (MTU 9000) improve throughput in data centers.
