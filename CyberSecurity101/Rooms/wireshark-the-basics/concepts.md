# Wireshark: The Basics — Concepts

## Packet Capture
The process of intercepting and logging network traffic as it traverses a network interface. Packets are stored in pcap or pcapng format for analysis.

## Berkeley Packet Filter (BPF)
A syntax for filtering packets at the kernel level before they are passed to the application. BPF filters are efficient and reduce capture file size. Example: `tcp port 80`.

## Display Filter
A Wireshark-specific filter syntax used to hide or show packets based on protocol field values after capture. More expressive than BPF and supports field-level conditions.

## TCP Stream Following
A Wireshark feature that reassembles the full TCP conversation between two hosts, displaying the application-layer data (e.g., HTTP request and response as a single stream).

## Protocol Hierarchy
A Wireshark statistics view showing the percentage and count of packets using each protocol. Useful for understanding traffic composition at a glance.

## Promiscuous Mode
A mode in which the network interface captures all packets on the wire, not just those addressed to its MAC address. Required for full network monitoring.
