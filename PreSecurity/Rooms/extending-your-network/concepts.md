# Concepts: Extending Your Network

## 1. NAT (Network Address Translation)
NAT maps private IP addresses to a public IP address, allowing multiple devices on a private network to share a single public IP for internet access. NAT conserves public IPv4 addresses and adds a layer of privacy by hiding internal IPs.

## 2. PAT (Port Address Translation)
PAT is a form of NAT that tracks connections by port numbers. It assigns unique source ports to each internal connection so responses can be correctly routed back. Most home routers use PAT to share one public IP among all connected devices.

## 3. DHCP (Dynamic Host Configuration Protocol)
DHCP automatically assigns IP addresses, subnet masks, default gateways, and DNS servers to devices on a network. Without DHCP, every device would need manual IP configuration. DHCP uses a four-step DORA process and assigns leases with expiration times.

## 4. The DORA Process
Discovery: the client broadcasts a DHCPDISCOVER message. Offer: DHCP servers respond with DHCPOFFER (proposed IP). Request: the client broadcasts DHCPREQUEST for the chosen offer. Acknowledgment: the server sends DHCPACK with configuration and lease time.

## 5. VPN (Virtual Private Network)
A VPN creates an encrypted tunnel between two endpoints over an untrusted network (like the internet). It provides confidentiality, integrity, and sometimes anonymity. Common use cases include secure remote access, bypassing geo-restrictions, and connecting branch offices.

## 6. Subnetting and CIDR
Subnetting divides a larger network into smaller, manageable subnets. CIDR notation (e.g., 192.168.1.0/24) specifies the network prefix length. The network mask (/24 = 255.255.255.0) determines which part of the address is the network portion and which is the host portion.

## 7. Routing and Default Gateway
Routing is the process of forwarding packets from one network to another. Each device maintains a routing table. The default gateway is the router that handles traffic destined for networks beyond the local subnet. Dynamic routing protocols (OSPF, BGP) automate route learning.

## 8. Network Firewalls
Firewalls filter network traffic based on rules. Stateless firewalls examine individual packets. Stateful firewalls track connection state and allow return traffic automatically. Next-generation firewalls (NGFW) add application awareness, intrusion prevention, and deep packet inspection.
