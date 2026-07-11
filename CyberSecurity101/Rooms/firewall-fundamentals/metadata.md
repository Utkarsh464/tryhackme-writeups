# Firewall Fundamentals

## Room Information
- **URL**: https://tryhackme.com/room/firewallfundamentals
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

## Description

Firewall Fundamentals covers one of the most essential components of network security: the firewall. Firewalls are security devices that monitor and control incoming and outgoing network traffic based on predetermined security rules. They serve as the first line of defense in network security, establishing a barrier between trusted internal networks and untrusted external networks like the internet. This room traces the evolution of firewall technology from simple packet filters to sophisticated next-generation firewalls. Packet filtering firewalls, the earliest type, inspect individual packet headers and make allow/deny decisions based on source and destination IP addresses, ports, and protocols. They are fast but cannot understand the context or state of connections. Stateful inspection firewalls track the state of active connections and make decisions based on the context of the traffic. They maintain a state table of all active sessions and only allow packets that belong to a legitimate established connection. Application-layer firewalls (proxies) inspect the content of application protocols, providing deep visibility into HTTP, FTP, SMTP, and other protocols. Web Application Firewalls (WAFs) specialize in protecting web applications from attacks like SQL injection and XSS. Next-Generation Firewalls (NGFWs) combine traditional firewall capabilities with integrated intrusion prevention, application awareness and control, SSL/TLS inspection, identity-based policies, and threat intelligence feeds. The room covers firewall rule creation: defining source zones, destination zones, source addresses, destination addresses, services (ports/protocols), and actions (allow, deny, reject). Learners explore zone-based security architectures: inside (trusted), outside (untrusted), and DMZ (semi-trusted for public-facing services). Network Address Translation (NAT) and port forwarding are explained as essential firewall functions for mapping private addresses to public addresses and directing external traffic to internal services. Firewall logging and monitoring are covered for auditing traffic patterns and detecting blocked attack attempts. Deployment architectures include single-firewall designs for small networks, multi-firewall designs with DMZ segments, and cloud firewall services like AWS Security Groups and Azure Network Security Groups.

## Objectives
- Understand firewall types and their evolution
- Create and manage firewall rules
- Understand zone-based security architectures
- Configure NAT and port forwarding
- Analyze firewall logs for security events
- Design firewall deployments for different network sizes

## Tools
- iptables/nftables (Linux firewall)
- pfSense or OPNsense (open-source firewall distributions)
- Windows Firewall
- Wireshark (for traffic analysis)

## Concepts
- Packet filtering vs stateful inspection
- Application-layer firewalls and proxies
- Next-generation firewalls (NGFW)
- Zone-based security (inside, outside, DMZ)
- Network Address Translation (NAT) and port forwarding
- Default deny vs default allow policies
- Firewall rule ordering and optimization
- Web Application Firewalls (WAF)
