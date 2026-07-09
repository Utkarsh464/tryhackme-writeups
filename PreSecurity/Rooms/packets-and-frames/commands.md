# Commands: Packets and Frames

## Packet Capture

| Command | Description |
|---------|-------------|
| `sudo tcpdump -i eth0 -X` | Capture packets and print hex+ASCII output |
| `sudo tcpdump -i eth0 port 80` | Capture only HTTP traffic on port 80 |
| `sudo tcpdump -i eth0 -w capture.pcap` | Write captured packets to a file |

## Packet Analysis

| Command | Description |
|---------|-------------|
| `tcpdump -r capture.pcap -n` | Read a packet capture file |
| `tshark -r capture.pcap -Y "tcp.flags.syn==1"` | Filter for SYN packets in a pcap with tshark |
