# Networking Concepts — Concepts

## OSI Model
A seven-layer conceptual framework (Physical, Data Link, Network, Transport, Session, Presentation, Application) that standardizes network communication. Each layer provides services to the layer above and receives services from the layer below.

## TCP/IP Model
A four-layer model (Network Interface, Internet, Transport, Application) that reflects the actual protocol suite used on the internet. It is more practical than the OSI model but covers the same principles.

## Encapsulation
The process by which data is wrapped with protocol headers as it travels down the protocol stack. Each layer adds its own header, and the receiving device strips headers in reverse order.

## IPv4 Addressing
A 32-bit address scheme that uniquely identifies devices on a network. Written as four decimal octets (e.g., 192.168.1.1).

## Subnetting
The practice of dividing a larger network into smaller subnetworks using a subnet mask. Improves performance and security by limiting broadcast domains.

## MAC Address
A 48-bit hardware address assigned to network interfaces. Operates at the Data Link layer and is used for local network delivery.

## Address Resolution Protocol (ARP)
A protocol used to map an IPv4 address to a MAC address on a local network. ARP broadcasts a request and the target device responds with its MAC address.
