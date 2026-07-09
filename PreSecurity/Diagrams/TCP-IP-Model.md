# TCP/IP Model

```mermaid
graph TD
    App[Application] --> Trans[Transport]
    Trans --> Internet[Internet]
    Internet --> NetAccess[Network Access]

    App -->|HTTP, FTP, DNS, SMTP, SSH| AppP[HTTP, FTP, DNS, SMTP, SSH]
    Trans -->|TCP, UDP| TransP[TCP, UDP]
    Internet -->|IP, ICMP, ARP| InternetP[IP, ICMP, ARP]
    NetAccess -->|Ethernet, Wi-Fi, PPP| NetAccessP[Ethernet, Wi-Fi, PPP]

    OSI_App[OSI 5-7: Application, Presentation, Session] -.-> App
    OSI_Trans[OSI 4: Transport] -.-> Trans
    OSI_Net[OSI 3: Network] -.-> Internet
    OSI_NetAcc[OSI 1-2: Physical, Data Link] -.-> NetAccess
```

The TCP/IP model is the practical implementation used by the modern internet. It condenses the OSI model's seven layers into four: Application (combining OSI layers 5-7), Transport (OSI layer 4), Internet (OSI layer 3), and Network Access (OSI layers 1-2).
