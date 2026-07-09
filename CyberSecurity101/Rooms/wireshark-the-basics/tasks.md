# Wireshark: The Basics — Tasks

## Task 1: Introduction and Interface
- **Purpose:** Familiarize with the Wireshark interface and its key components.
- **Skills:** Interface navigation, capture configuration.
- **Commands:** None (GUI-based).
- **Theory:** Wireshark displays packets in three panes: the packet list pane (summary), the packet details pane (protocol tree), and the packet bytes pane (hex dump). Key interface elements include the toolbar, display filter bar, and status bar.

## Task 2: Capturing Traffic
- **Purpose:** Learn to capture live network traffic on a selected interface.
- **Skills:** Interface selection, capture start/stop, capture file management.
- **Commands:** None (GUI-based).
- **Theory:** Select the correct network interface for capture. Configure capture options like promiscuous mode (captures all packets the interface sees, not just those addressed to it). Save captures as pcap or pcapng files for later analysis.

## Task 3: Capture Filters (BPF)
- **Purpose:** Apply Berkeley Packet Filter syntax to capture only specific traffic.
- **Skills:** BPF syntax writing, filter compilation.
- **Commands:** None (GUI-based).
- **Theory:** BPF filters are applied before capture begins, reducing the volume of captured data. Examples: `host 192.168.1.1`, `port 80`, `tcp`, `udp port 53`, `not arp`.

## Task 4: Display Filters
- **Purpose:** Use display filters to isolate packets of interest after capture.
- **Skills:** Display filter syntax, filter combination (and/or/not), field-specific filtering.
- **Commands:** None (GUI-based).
- **Theory:** Display filters use a more expressive syntax than BPF. Examples: `http.request`, `tcp.port == 443`, `ip.addr == 10.0.0.1`, `dns.qry.name contains "google"`. Filters can be combined: `http and ip.src == 192.168.1.1`.

## Task 5: Following Streams and Protocol Hierarchy
- **Purpose:** Reconstruct application-layer conversations and analyze protocol distribution.
- **Skills:** TCP stream follow, protocol hierarchy statistics.
- **Commands:** None (GUI-based).
- **Theory:** Right-clicking a packet and selecting Follow TCP Stream reconstructs the full conversation in order. Protocol Hierarchy Statistics shows the percentage of traffic using each protocol, helping identify dominant protocols.
