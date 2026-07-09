# TCP/IP Model (4-Layer) vs OSI Model with Protocol Mappings

```mermaid
graph LR
    subgraph OSI["OSI Model (7 Layers)"]
        O7["7. Application"]
        O6["6. Presentation"]
        O5["5. Session"]
        O4["4. Transport"]
        O3["3. Network"]
        O2["2. Data Link"]
        O1["1. Physical"]
    end

    subgraph TCPIP["TCP/IP Model (4 Layers)"]
        T4["4. Application"]
        T3["3. Transport"]
        T2["2. Internet"]
        T1["1. Network Access"]
    end

    O7 --- T4
    O6 --- T4
    O5 --- T4
    O4 --- T3
    O3 --- T2
    O2 --- T1
    O1 --- T1

    subgraph PROTO["Protocol Mappings"]
        APP["Application: HTTP, HTTPS, FTP, SMTP, DNS, DHCP, SNMP, SSH, Telnet"]
        TRAN["Transport: TCP (segments), UDP (datagrams)"]
        INET["Internet: IP (IPv4, IPv6), ICMP, ARP, IGMP"]
        NETACC["Network Access: Ethernet, Wi-Fi, PPP, DSL, Frame Relay"]
    end

    T4 --- APP
    T3 --- TRAN
    T2 --- INET
    T1 --- NETACC
```

The TCP/IP model is the practical networking framework used by the modern Internet, consisting of four layers that map roughly to the seven-layer OSI model. **Layer 4 (Application)** combines the OSI Application, Presentation, and Session layers into a single layer where high-level protocols like HTTP, FTP, DNS, and SMTP operate. Data is exchanged in messages or streams. **Layer 3 (Transport)** corresponds directly to the OSI Transport layer and handles end-to-end communication using TCP for reliable, connection-oriented delivery and UDP for fast, connectionless delivery. The data unit at this layer is a segment (TCP) or datagram (UDP). **Layer 2 (Internet)** maps to the OSI Network layer and is responsible for logical addressing, routing, and packet forwarding using IP (both IPv4 and IPv6), ICMP for diagnostics, and ARP for address resolution. Data is organized into packets. **Layer 1 (Network Access)** combines the OSI Data Link and Physical layers, handling the physical transmission of data over network hardware such as Ethernet cables, Wi-Fi radios, and DSL modems. The data unit here is a frame. The TCP/IP model is less rigid than OSI and was designed specifically for interoperability across heterogeneous networks, which is why it became the foundation of the Internet.
