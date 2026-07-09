# Networking Cheat Sheet

## OSI Model (7 Layers)
| Layer | Name | Example Protocols |
|-------|------|------------------|
| 7 | Application | HTTP, FTP, SMTP, DNS, SSH |
| 6 | Presentation | SSL/TLS, JPEG, ASCII |
| 5 | Session | NetBIOS, RPC, PPTP |
| 4 | Transport | TCP, UDP |
| 3 | Network | IP, ICMP, OSPF, BGP |
| 2 | Data Link | Ethernet, ARP, MAC |
| 1 | Physical | Cables, Hubs, Repeaters |

## TCP/IP Model (4 Layers)
| Layer | Equivalent OSI | Protocols |
|-------|----------------|-----------|
| Application | 7,6,5 | HTTP, DNS, FTP, SMTP |
| Transport | 4 | TCP, UDP |
| Internet | 3 | IP, ICMP, ARP |
| Network Access | 2,1 | Ethernet, WiFi |

## Common Ports
| Port | Protocol | Service |
|------|----------|---------|
| 20/21 | TCP | FTP |
| 22 | TCP | SSH |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP |
| 53 | TCP/UDP | DNS |
| 67/68 | UDP | DHCP |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 143 | TCP | IMAP |
| 161 | UDP | SNMP |
| 389 | TCP/UDP | LDAP |
| 443 | TCP | HTTPS |
| 445 | TCP | SMB |
| 993 | TCP | IMAPS |
| 995 | TCP | POP3S |
| 1433 | TCP | MSSQL |
| 1521 | TCP | Oracle DB |
| 2049 | TCP/UDP | NFS |
| 3306 | TCP | MySQL |
| 3389 | TCP | RDP |
| 5432 | TCP | PostgreSQL |
| 5900 | TCP | VNC |
| 6379 | TCP | Redis |
| 8080 | TCP | HTTP-Proxy |
| 8443 | TCP | HTTPS-Alt |
| 27017 | TCP | MongoDB |

## TCP vs UDP
| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Guaranteed delivery | Best-effort |
| Ordering | Preserves order | No ordering |
| Speed | Slower (overhead) | Faster |
| Use cases | Web, email, file transfer | Streaming, DNS, VoIP |

## DNS Record Types
| Record | Purpose | Example |
|--------|---------|---------|
| A | IPv4 address | `example.com A 192.0.2.1` |
| AAAA | IPv6 address | `example.com AAAA 2001:db8::1` |
| CNAME | Canonical name (alias) | `www CNAME example.com` |
| MX | Mail exchange | `@ MX 10 mail.example.com` |
| NS | Name server | `example.com NS ns1.example.com` |
| TXT | Text data | `@ TXT "v=spf1 include:_spf.google.com"` |
| PTR | Reverse lookup | `1.2.0.192.in-addr.arpa PTR example.com` |
| SOA | Start of authority | Zone transfer info |
| SRV | Service location | `_sip._tcp.example.com SRV 10 5 5060 sipserver` |

## Subnetting Reference
| CIDR | Subnet Mask | IPs | Usable | Class |
|------|-------------|-----|--------|-------|
| /32 | 255.255.255.255 | 1 | 1 | - |
| /30 | 255.255.255.252 | 4 | 2 | - |
| /29 | 255.255.255.248 | 8 | 6 | - |
| /28 | 255.255.255.240 | 16 | 14 | - |
| /27 | 255.255.255.224 | 32 | 30 | - |
| /26 | 255.255.255.192 | 64 | 62 | - |
| /25 | 255.255.255.128 | 128 | 126 | - |
| /24 | 255.255.255.0 | 256 | 254 | C |
| /23 | 255.255.254.0 | 512 | 510 | - |
| /22 | 255.255.252.0 | 1024 | 1022 | - |
| /21 | 255.255.248.0 | 2048 | 2046 | - |
| /20 | 255.255.240.0 | 4096 | 4094 | - |
| /19 | 255.255.224.0 | 8192 | 8190 | - |
| /18 | 255.255.192.0 | 16384 | 16382 | - |
| /17 | 255.255.128.0 | 32768 | 32766 | - |
| /16 | 255.255.0.0 | 65536 | 65534 | B |

## Private IP Ranges
| Range | CIDR |
|-------|------|
| 10.0.0.0 - 10.255.255.255 | 10.0.0.0/8 |
| 172.16.0.0 - 172.31.255.255 | 172.16.0.0/12 |
| 192.168.0.0 - 192.168.255.255 | 192.168.0.0/16 |

## Common Networking Commands
| Command | Description |
|---------|-------------|
| `ping -c 4 host` | ICMP echo test |
| `traceroute host` (Linux) | Route tracing |
| `tracert host` (Windows) | Route tracing |
| `nslookup domain` | DNS lookup |
| `dig domain ANY` | Detailed DNS query |
| `dig -x IP` | Reverse DNS |
| `netstat -ano` | Active connections |
| `ss -tulnp` | Listening ports |
| `tcpdump -i eth0 port 80` | Packet capture |
| `curl -v http://host` | HTTP request debug |
| `whois domain` | Domain registration info |
