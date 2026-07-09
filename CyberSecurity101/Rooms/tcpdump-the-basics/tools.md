# Tcpdump: The Basics — Tools

- **Tcpdump:** The primary tool for this room. A command-line packet analyzer using libpcap. Standard on virtually all Linux and macOS systems.
- **libpcap:** The underlying packet capture library that Tcpdump (and Wireshark) use. Provides the low-level interface to network drivers.
- **Wireshark / tshark:** Can be used to further analyze pcap files created by Tcpdump, providing a graphical interface and additional dissection capabilities.
- **tcpreplay:** A tool for replaying pcap files back onto a network, useful for testing NIDS and other monitoring tools.
- **tcpick / tcpflow:** Tools that reassemble TCP streams from pcap files and extract the application-layer data.
