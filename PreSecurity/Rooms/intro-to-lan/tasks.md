# Tasks: Intro to LAN

## Task 1: Ethernet
**Purpose:** Learn the fundamentals of Ethernet networking.

**Skills:** Understanding wired networking.

**Theory:** Ethernet is the most common technology for wired LANs. It defines how devices format and transmit data over cables using frames. Ethernet operates at the data link layer (Layer 2) and uses MAC addresses for device identification.

**Commands:** N/A

---

## Task 2: MAC Addresses
**Purpose:** Understand MAC addresses and their structure.

**Skills:** Layer 2 addressing.

**Theory:** A MAC (Media Access Control) address is a 48-bit unique identifier assigned to every network interface card. It is typically written as 6 pairs of hexadecimal digits (e.g., 00:1A:2B:3C:4D:5E). The first 24 bits identify the manufacturer (OUI).

**Commands:** `ip link show`, `ifconfig`

---

## Task 3: ARP Protocol
**Purpose:** Learn how ARP resolves IP addresses to MAC addresses.

**Skills:** Address resolution.

**Theory:** ARP (Address Resolution Protocol) maps a device's IP address to its MAC address on a local network. When a device knows the target IP but not the MAC, it broadcasts an ARP request; the target responds with its MAC address. The mapping is cached in the ARP table.

**Commands:** `arp -a`

---

## Task 4: Switches
**Purpose:** Understand how switches forward traffic.

**Skills:** LAN switching.

**Theory:** Switches operate at Layer 2 and use MAC address tables to forward frames only to the correct port. This makes them more efficient than hubs, which broadcast to all ports. Switches learn MAC addresses by inspecting the source address of incoming frames.

**Commands:** N/A

---

## Task 5: Collision and Broadcast Domains
**Purpose:** Differentiate between collision and broadcast domains.

**Skills:** Network segmentation concepts.

**Theory:** A collision domain is a network segment where two devices cannot transmit simultaneously. Switches eliminate collision domains per port. A broadcast domain is a segment where a broadcast frame is received by all devices. Routers separate broadcast domains.

**Commands:** N/A

---
