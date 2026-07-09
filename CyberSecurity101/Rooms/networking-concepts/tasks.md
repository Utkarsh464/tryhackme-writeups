# Networking Concepts — Tasks

## Task 1: Introduction to the OSI Model
- **Purpose:** Understand the seven-layer OSI model and how each layer contributes to network communication.
- **Skills:** Model memorization, layer identification, understanding encapsulation.
- **Commands:** None.
- **Theory:** The OSI model is a conceptual framework that standardizes network communication into seven distinct layers: Physical, Data Link, Network, Transport, Session, Presentation, and Application. Each layer has a specific function and communicates with the layers directly above and below it. Encapsulation occurs as data moves down the stack, with each layer adding its own header.

## Task 2: The TCP/IP Model
- **Purpose:** Compare and contrast the TCP/IP model with the OSI model and understand the de facto standard for internet communication.
- **Skills:** Model comparison, protocol mapping.
- **Commands:** None.
- **Theory:** The TCP/IP model condenses the OSI layers into four: Network Interface, Internet, Transport, and Application. This model reflects the actual protocol suite used on the internet. Key protocols like TCP, UDP, IP, and HTTP are mapped to their respective layers.

## Task 3: IP Addressing and Subnetting
- **Purpose:** Grasp the structure of IPv4 and IPv6 addresses and how subnetting divides networks into smaller segments.
- **Skills:** Address format recognition, subnet mask calculation, network/host portion identification.
- **Commands:** None.
- **Theory:** An IPv4 address is a 32-bit number typically written in dotted decimal notation. The subnet mask determines which portion of the address identifies the network and which identifies the host. Subnetting improves network efficiency and security by segmenting traffic.

## Task 4: MAC Addresses and ARP
- **Purpose:** Understand the role of MAC addresses at the data link layer and how ARP resolves IP addresses to MAC addresses.
- **Skills:** Address resolution, MAC address format recognition.
- **Commands:** None.
- **Theory:** MAC addresses are 48-bit hardware addresses burned into network interfaces. The Address Resolution Protocol (ARP) maps an IP address to the corresponding MAC address on a local network segment, enabling frames to be delivered to the correct device.
