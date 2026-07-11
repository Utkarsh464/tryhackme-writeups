# REMnux: Getting Started — Commands

| Command | Description |
|---------|-------------|
| `file sample.exe` | Identify the file type and format |
| `strings sample.exe` | Extract human-readable strings from a binary |
| `strings -n 8 sample.exe` | Extract strings of at least 8 characters |
| `xxd sample.bin | head -20` | Display hexadecimal dump of a file |
| `radare2 sample.exe` | Open a binary in the radare2 reverse engineering framework |
| `oleid suspicious.doc` | Scan an OLE file (Office doc) for risky indicators |
| `olevba suspicious.doc` | Extract and analyze VBA macros from Office documents |
| `mraptor suspicious.doc` | Assess whether VBA macros are suspicious |
| `oledump.py suspicious.doc` | Dump streams from OLE files |
| `pdfid.py sample.pdf` | Scan a PDF for key structural indicators |
| `pdf-parser.py sample.pdf` | Parse and analyze PDF structure objects |
| `volatility -f mem.dmp imageinfo` | Identify the OS profile from a memory dump |
| `volatility -f mem.dmp --profile=Win10x64 pslist` | List running processes from a memory dump |
| `volatility -f mem.dmp --profile=Win10x64 netscan` | List network connections from a memory dump |
| `tcpdump -i eth0 -w capture.pcap` | Capture live network traffic to a file |
| `tcpdump -r capture.pcap` | Read and display a packet capture file |
| `wireshark capture.pcap` | Open a packet capture in Wireshark GUI |
| `ngrep -d eth0 "POST" port 80` | Search live traffic for patterns |
| `lsb_release -a` | Display REMnux distribution information |
