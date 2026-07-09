# TCP 3-Way Handshake

```mermaid
sequenceDiagram
    participant Client
    participant Server

    Client->>Server: SYN (SEQ=x)
    Note over Client,Server: Client sends SYN with random sequence number x
    Server->>Client: SYN-ACK (SEQ=y, ACK=x+1)
    Note over Server,Client: Server responds with SYN, ACK, and its own sequence number y
    Client->>Server: ACK (SEQ=x+1, ACK=y+1)
    Note over Client,Server: Client acknowledges, connection established
    Note over Client,Server: Connection Established — Data Transfer Begins
```

The TCP three-way handshake establishes a reliable connection between client and server before data transfer begins. The process involves SYN (synchronize), SYN-ACK (synchronize-acknowledge), and ACK (acknowledge) messages, ensuring both sides are ready to communicate and have agreed on initial sequence numbers.
