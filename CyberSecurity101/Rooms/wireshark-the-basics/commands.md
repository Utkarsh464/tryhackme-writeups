# Wireshark: The Basics — Commands

Wireshark is primarily GUI-driven, but the following commands are useful in conjunction with it:

| Command | Description |
|---------|-------------|
| `wireshark` | Launch the Wireshark GUI |
| `tshark` | Command-line version of Wireshark for scripting |
| `tshark -r capture.pcap` | Read and analyze a pcap file from the command line |
| `tshark -i eth0 -w output.pcap` | Capture traffic directly to a file using tshark |
| `tshark -Y "http.request" -r capture.pcap` | Apply a display filter with tshark |
| `mergecap -w output.pcap input1.pcap input2.pcap` | Merge multiple pcap files |
| `editcap -c 1000 input.pcap output.pcap` | Split a pcap file into smaller chunks |
