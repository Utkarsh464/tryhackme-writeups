# Module 5: Networking - Quick Reference

## OSI Model (7 Layers)
- **L7 - Application**: HTTP, FTP, SMTP, DNS, SSH - User-facing protocols
- **L6 - Presentation**: Encryption, compression, data formatting (SSL/TLS)
- **L5 - Session**: Session management, NetBIOS, RPC
- **L4 - Transport**: TCP/UDP, segmentation, reliability, flow control
- **L3 - Network**: IP, routing, logical addressing (routers)
- **L2 - Data Link**: Ethernet, MAC addresses, frames (switches)
- **L1 - Physical**: Cables, signals, bits (hubs, repeaters)

## TCP/IP Model (4 Layers)
- **Application** (combines L5-7): HTTP, FTP, DNS, SMTP, SSH
- **Transport**: TCP (reliable), UDP (fast)
- **Internet** (network): IP, ICMP, ARP, routing
- **Network Access** (link): Ethernet, WiFi, PPP

## TCP vs UDP
| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable (retransmission) | Unreliable |
| Ordering | Guaranteed | Not guaranteed |
| Header | 20-60 bytes | 8 bytes |
| Speed | Slower (overhead) | Faster |
| Use cases | HTTP, SSH, FTP, SMTP | DNS, VoIP, streaming, gaming |

## TCP 3-Way Handshake
1. Client sends **SYN** (seq=x)
2. Server responds **SYN-ACK** (seq=y, ack=x+1)
3. Client sends **ACK** (ack=y+1) → Connection established

## Common Ports to Memorize
- **20/21** - FTP (data/control)
- **22** - SSH
- **23** - Telnet
- **25** - SMTP
- **53** - DNS (TCP + UDP)
- **67/68** - DHCP
- **80** - HTTP
- **110** - POP3
- **143** - IMAP
- **161/162** - SNMP
- **389** - LDAP
- **443** - HTTPS
- **445** - SMB
- **465/587** - SMTP over TLS
- **636** - LDAPS
- **993** - IMAPS
- **995** - POP3S
- **1433** - MSSQL
- **3306** - MySQL
- **3389** - RDP
- **5432** - PostgreSQL
- **5900** - VNC
- **6379** - Redis
- **8080** - HTTP alternate
- **8443** - HTTPS alternate
- **27017** - MongoDB

## DNS Record Types
- **A** - IPv4 address
- **AAAA** - IPv6 address
- **CNAME** - Canonical name (alias)
- **MX** - Mail exchanger (with priority)
- **NS** - Nameserver
- **TXT** - Text (SPF, DKIM, DMARC)
- **PTR** - Pointer (reverse DNS)
- **SOA** - Start of Authority
- **SRV** - Service location
- **CAA** - Certificate Authority Authorization

## DHCP DORA Process
1. **D**iscover - Client broadcasts "need IP"
2. **O**ffer - Server offers IP configuration
3. **R**equest - Client requests offered IP
4. **A**cknowledge - Server confirms

## Subnetting Cheat Sheet
| CIDR | Subnet Mask | Hosts | Use |
|------|-------------|-------|-----|
| /24 | 255.255.255.0 | 254 | Small LAN |
| /16 | 255.255.0.0 | 65,534 | Large network |
| /8 | 255.0.0.0 | 16,777,214 | Huge network |
| /30 | 255.255.255.252 | 2 | Point-to-point |
| /32 | 255.255.255.255 | 1 | Single host |
| /28 | 255.255.255.240 | 14 | Small subnet |
| /27 | 255.255.255.224 | 30 | Medium small |
| /29 | 255.255.255.248 | 6 | Very small |

**Formula**: Valid hosts = 2^(32 - prefix) - 2

## Private IP Ranges
- **10.0.0.0/8** - 10.0.0.0 to 10.255.255.255 (16M hosts)
- **172.16.0.0/12** - 172.16.0.0 to 172.31.255.255 (1M hosts)
- **192.168.0.0/16** - 192.168.0.0 to 192.168.255.255 (65k hosts)
- **169.254.0.0/16** - Link-local (APIPA)
- **127.0.0.0/8** - Loopback (localhost)

## HTTP Methods
- **GET** - Retrieve resource
- **POST** - Submit data (creates)
- **PUT** - Replace/update resource
- **PATCH** - Partial update
- **DELETE** - Remove resource
- **HEAD** - GET without body
- **OPTIONS** - Supported methods
- **CONNECT** - Tunnel (HTTPS proxy)

## HTTP Status Codes
- **1xx** Informational: 100 Continue, 101 Switching Protocols
- **2xx** Success: 200 OK, 201 Created, 204 No Content
- **3xx** Redirect: 301 Moved Permanently, 302 Found, 304 Not Modified
- **4xx** Client Error: 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 405 Method Not Allowed, 429 Too Many Requests
- **5xx** Server Error: 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable, 504 Gateway Timeout

## Key Protocols
- **ARP** - Resolves IP to MAC (broadcast request, unicast reply)
- **ICMP** - Error reporting, diagnostics (ping uses ICMP echo/reply)
- **NAT** - Maps private IPs to public (PAT uses ports for many-to-one)
- **DHCP** - DORA for automatic IP assignment
- **SSL/TLS** - Encryption, authentication, integrity for HTTPS (handshake with certificate exchange)
- **SMTP** - Email sending (port 25/587)
- **POP3/IMAP** - Email retrieval (POP3 downloads, IMAP syncs)
- **SNMP** - Network management (OIDs, MIBs)
- **NTP** - Time synchronization (port 123, stratum levels)

## Network Devices
- **Hub** - L1, broadcasts to all ports, half-duplex
- **Switch** - L2, MAC address learning, full-duplex, VLANs
- **Router** - L3, IP routing, connects networks, NAT
- **Firewall** - L3-L7, traffic filtering, stateful inspection
- **Load Balancer** - Distributes traffic across servers
- **Proxy** - Intermediary for requests (forward/reverse)
- **Modem** - Modulates digital to analog signals
- **Access Point** - Wireless connectivity
- **Bridge** - Connects two network segments

## Troubleshooting Commands
- `ip a / ifconfig` - Interface configuration
- `ping` - Basic connectivity
- `traceroute / tracert` - Path to destination
- `nslookup / dig` - DNS queries
- `curl -v / wget` - HTTP testing
- `nc -zv host port` - Port connectivity
- `ss -tuln / netstat -an` - Listening ports
- `tcpdump -i eth0` - Packet capture
- `iptables -L -n` - Firewall rules
- `route -n / ip route` - Routing table
- `arp -a` - ARP cache
- `mtr host` - Combines ping + traceroute

## Wireless Security
- **WEP** - Broken (RC4, cracked in minutes)
- **WPA** - TKIP, improved but vulnerable
- **WPA2** - AES-CCMP (standard since 2006)
- **WPA3** - SAE, forward secrecy, protects against dictionary attacks
- **Attacks**: Evil Twin, KRACK, Deauth, WPS PIN brute force
