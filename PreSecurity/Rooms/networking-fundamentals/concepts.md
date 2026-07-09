# Concepts: Networking Fundamentals

## 1. What is a Network?
A network is a collection of interconnected devices that can communicate and share resources. Networks use wired (Ethernet, fiber) or wireless (Wi-Fi, cellular) connections and rely on protocols to standardize communication.

## 2. Local Area Network (LAN)
A LAN connects devices within a limited geographic area such as a home, school, or office building. LANs offer high speed and low latency, typically use Ethernet or Wi-Fi, and are owned and managed by a single organization.

## 3. Wide Area Network (WAN)
A WAN spans a large geographic area, often connecting multiple LANs across cities or countries. The internet is the largest WAN. WAN connections are slower and more expensive than LAN connections due to the distances involved.

## 4. Metropolitan Area Network (MAN)
A MAN covers a city or large campus, bridging the gap between LAN and WAN. MANs are often used by city governments or ISPs to connect multiple locations within a metropolitan region using high-speed fiber connections.

## 5. Star Topology
All devices connect to a central hub or switch. Each device has a dedicated connection, so a single device failure does not affect others. However, the central switch is a single point of failure.

## 6. Bus Topology
All devices connect to a single backbone cable. Data travels along the backbone and each device checks if the data is addressed to it. Bus topology is inexpensive but a break in the backbone brings down the entire network.

## 7. Ring Topology
Devices are connected in a closed loop, with data traveling in one direction. Each device acts as a repeater. A break in the ring disrupts all traffic beyond that point.

## 8. Mesh Topology
Every device connects directly to every other device. Mesh topology provides maximum redundancy — if one link fails, data can take an alternate path. The high cabling cost makes it impractical for large networks.
