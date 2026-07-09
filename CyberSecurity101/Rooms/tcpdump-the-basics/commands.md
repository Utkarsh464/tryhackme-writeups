# Tcpdump: The Basics — Commands

| Command | Description |
|---------|-------------|
| `tcpdump -D` | List available network interfaces |
| `tcpdump -i eth0` | Capture packets on interface eth0 |
| `tcpdump -i eth0 -c 100` | Capture only 100 packets then stop |
| `tcpdump -i eth0 host 192.168.1.1` | Capture traffic to/from a specific host |
| `tcpdump -i eth0 port 22` | Capture traffic on a specific port |
| `tcpdump -i eth0 tcp` | Capture only TCP traffic |
| `tcpdump -i eth0 -w capture.pcap` | Write captured packets to a file |
| `tcpdump -r capture.pcap` | Read and display packets from a file |
| `tcpdump -r capture.pcap -v` | Read with verbosity |
| `tcpdump -r capture.pcap -X` | Print hex and ASCII dump of packets |
| `tcpdump -i eth0 -n` | Do not resolve hostnames (faster, more secure) |
| `tcpdump -i eth0 -nn` | Do not resolve hostnames or port names |
| `tcpdump -i eth0 src net 10.0.0.0/8` | Capture traffic from a specific source network |
