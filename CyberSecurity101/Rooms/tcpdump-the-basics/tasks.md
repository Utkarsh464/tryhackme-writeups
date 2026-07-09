# Tcpdump: The Basics — Tasks

## Task 1: Introduction and Basic Capture
- **Purpose:** Learn the basic syntax of Tcpdump and capture packets on an interface.
- **Skills:** Interface selection, basic capture command, understanding output format.
- **Commands:** `tcpdump -i eth0`, `tcpdump -D`
- **Theory:** Tcpdump requires root privileges to capture in promiscuous mode. The `-i` flag specifies the interface. `-D` lists available interfaces. Output shows timestamp, source/destination IP and port, protocol flags, and packet length.

## Task 2: BPF Filters
- **Purpose:** Apply Berkeley Packet Filters to capture only relevant traffic.
- **Skills:** Filter syntax for hosts, ports, protocols, and combinations.
- **Commands:** `tcpdump -i eth0 host 192.168.1.1`, `tcpdump -i eth0 port 80`, `tcpdump -i eth0 tcp`, `tcpdump -i eth0 "host 10.0.0.1 and port 443"`
- **Theory:** BPF filters are applied as the last argument. Use `and`, `or`, `not` to combine expressions. Parentheses require quoting or escaping in the shell.

## Task 3: Saving and Reading Captures
- **Purpose:** Write captures to files for later analysis and read saved captures.
- **Skills:** File output with -w, file reading with -r.
- **Commands:** `tcpdump -i eth0 -w capture.pcap`, `tcpdump -r capture.pcap`
- **Theory:** The `-w` flag writes raw packets to a pcap file. The `-r` flag reads a pcap file as if it were a live capture. Saved captures can be shared or analyzed with other tools like Wireshark.

## Task 4: Controlling Output Verbosity
- **Purpose:** Adjust the level of detail in Tcpdump output.
- **Skills:** Verbosity flags (-v, -vv, -vvv, -q), output format understanding.
- **Commands:** `tcpdump -r capture.pcap -v`, `tcpdump -r capture.pcap -vv`, `tcpdump -r capture.pcap -q`
- **Theory:** More v's add increasing protocol detail. `-v` adds TTL and ID fields. `-vv` adds more protocol-specific details. `-q` reduces output to minimal information (quick mode).
