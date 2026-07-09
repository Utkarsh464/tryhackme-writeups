# OSI Model — 7 Layers with Protocols and Data Units

```mermaid
graph TD
    subgraph L7["Layer 7 — Application"]
        P7["HTTP, FTP, SMTP, DNS, DHCP, SSH, SNMP"]
        D7["Data Unit: Data"]
    end

    subgraph L6["Layer 6 — Presentation"]
        P6["SSL/TLS, JPEG, GIF, MPEG, ASCII, EBCDIC"]
        D6["Data Unit: Data"]
    end

    subgraph L5["Layer 5 — Session"]
        P5["NetBIOS, RPC, PPTP, SIP, SDP"]
        D5["Data Unit: Data"]
    end

    subgraph L4["Layer 4 — Transport"]
        P4["TCP, UDP, SCTP, DCCP"]
        D4["Data Unit: Segment / Datagram"]
    end

    subgraph L3["Layer 3 — Network"]
        P3["IP (IPv4, IPv6), ICMP, IGMP, OSPF, BGP, RIP"]
        D3["Data Unit: Packet"]
    end

    subgraph L2["Layer 2 — Data Link"]
        P2["Ethernet, PPP, HDLC, Frame Relay, ARP, MAC"]
        D2["Data Unit: Frame"]
    end

    subgraph L1["Layer 1 — Physical"]
        P1["RS-232, RJ45, V.34, 100BASE-TX, DSL, Bluetooth"]
        D1["Data Unit: Bits"]
    end

    L7 --> L6 --> L5 --> L4 --> L3 --> L2 --> L1
```

The OSI (Open Systems Interconnection) model is a conceptual framework used to understand network communication across seven distinct layers. Each layer serves a specific function and communicates with its peer layer on the remote host. **Layer 7 (Application)** provides network services directly to end-user applications and includes protocols like HTTP and DNS. **Layer 6 (Presentation)** handles data translation, encryption, and compression through formats like SSL/TLS and JPEG. **Layer 5 (Session)** manages sessions, dialogues, and checkpoints between applications using protocols such as RPC and NetBIOS. **Layer 4 (Transport)** ensures reliable or unreliable delivery of data segments via TCP or UDP respectively. **Layer 3 (Network)** handles logical addressing and routing of packets across networks using IP and routing protocols like OSPF and BGP. **Layer 2 (Data Link)** provides node-to-node data transfer and error detection using MAC addresses and Ethernet frames. **Layer 1 (Physical)** transmits raw bit streams over physical media like copper wire, fiber optics, or radio waves. Data flows down through the layers on the sender side and back up on the receiver side, with each layer adding its own header information in a process called encapsulation.
