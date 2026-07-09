# Concepts: Intro to LAN

## 1. Ethernet
Ethernet is the dominant wired networking technology for LANs. It operates at the data link layer (Layer 2) and defines frame formats, addressing, and access methods. Ethernet speeds range from 10 Mbps to 400 Gbps and beyond.

## 2. MAC Address
A Media Access Control address is a 48-bit hardware identifier burned into a network interface card. MAC addresses are unique per device and used for communication within a local network. The first 24 bits represent the Organizationally Unique Identifier (OUI) assigned to the manufacturer.

## 3. ARP (Address Resolution Protocol)
ARP translates IP addresses to MAC addresses on a local network. When a device needs to communicate with another device on the same subnet, it sends an ARP broadcast to discover the target's MAC address. Results are cached in the ARP table to reduce broadcasts.

## 4. ARP Spoofing
A malicious attack where an attacker sends fake ARP messages to associate their MAC address with the IP of a legitimate device. This allows the attacker to intercept, modify, or block traffic intended for that device (man-in-the-middle attack).

## 5. Network Switch
A switch forwards data frames based on MAC addresses. It maintains a CAM table (Content Addressable Memory) that maps MAC addresses to physical ports. Switches provide full-duplex communication and eliminate collisions on each port.

## 6. Collision Domain
A collision domain is a network segment where two devices cannot transmit simultaneously without causing a collision. Hubs create a single collision domain for all ports. Each switch port creates its own collision domain.

## 7. Broadcast Domain
A broadcast domain is a network segment where all devices receive broadcast frames. Routers and VLANs are used to separate broadcast domains. Large broadcast domains can cause performance issues due to excessive broadcast traffic.

## 8. Wireless LAN (WLAN)
WLANs use radio waves instead of cables to connect devices. Common standards include 802.11a/b/g/n/ac/ax (Wi-Fi 6). WLANs operate in half-duplex mode and share the medium, making them more susceptible to interference and eavesdropping than wired networks.
