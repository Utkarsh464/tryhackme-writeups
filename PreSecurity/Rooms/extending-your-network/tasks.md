# Tasks: Extending Your Network

## Task 1: NAT and PAT
**Purpose:** Learn how NAT and PAT enable multiple devices to share a single public IP.

**Skills:** Network address translation.

**Theory:** NAT translates private IP addresses (RFC 1918: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) to a public IP for internet access. PAT (Port Address Translation) extends NAT by using unique port numbers to map multiple internal connections to a single public IP.

**Commands:** N/A

---

## Task 2: DHCP (DORA Process)
**Purpose:** Understand how DHCP automates IP address assignment.

**Skills:** Network configuration.

**Theory:** DHCP uses the DORA process: Discovery (client broadcasts for a DHCP server), Offer (server offers an IP), Request (client requests the offered IP), Acknowledgment (server confirms). Leases have a time period after which the client must renew.

**Commands:** `dhclient eth0`

---

## Task 3: VPNs
**Purpose:** Learn how VPNs create secure connections over public networks.

**Skills:** Virtual private networking.

**Theory:** A VPN creates an encrypted tunnel between a client and a VPN server, protecting traffic from eavesdropping. Common VPN protocols include OpenVPN, IPsec, and WireGuard. VPNs are used for remote access, site-to-site connections, and privacy.

**Commands:** `sudo openvpn config.ovpn`

---

## Task 4: Subnetting
**Purpose:** Understand subnetting and CIDR notation.

**Skills:** IP address planning.

**Theory:** Subnetting divides a network into smaller subnets. CIDR notation (e.g., /24) indicates how many bits are in the network portion. A /24 network has 256 addresses (254 usable). Subnetting improves efficiency, security, and reduces broadcast traffic.

**Commands:** N/A

---

## Task 5: Routing and Firewalls
**Purpose:** Learn about routing tables, default gateways, and firewalls.

**Skills:** Network traffic management.

**Theory:** Routers use routing tables to forward packets toward their destination. The default gateway is the router that connects a local network to other networks. Firewalls filter traffic based on rules, operating stateless (packet filtering) or statefully (tracking connections).

**Commands:** `ip route show`, `sudo iptables -L`

---
