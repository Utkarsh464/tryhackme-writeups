# TCP 3-Way Handshake — Connection Establishment Sequence

```mermaid
sequenceDiagram
    participant Client
    participant Server

    Note over Client,Server: CLOSED
    Note over Client: SYN-SENT
    Client->>Server: SYN (seq=x)
    Note over Server: LISTEN
    Note over Server: SYN-RECEIVED
    Server-->>Client: SYN-ACK (seq=y, ack=x+1)
    Note over Client: ESTABLISHED
    Client->>Server: ACK (seq=x+1, ack=y+1)
    Note over Server: ESTABLISHED

    Note over Client,Server: Connection Established — Data Transfer Begins
    Client->>Server: Data Segment (seq=x+1, ack=y+1)
    Server-->>Client: Data Segment (seq=y+1, ack=x+2)

    Note over Client,Server: Connection Termination (4-Way Handshake)
    Client->>Server: FIN (seq=x+2)
    Server-->>Client: ACK (seq=y+2, ack=x+3)
    Server->>Client: FIN (seq=y+2)
    Client-->>Server: ACK (seq=x+3, ack=y+3)
    Note over Client,Server: CLOSED
```

The TCP three-way handshake is the process by which a TCP connection is reliably established between a client and a server before any data transfer occurs. The handshake ensures both sides are ready to communicate and synchronizes their sequence numbers. **Step 1 — SYN**: The client sends a TCP segment with the SYN (synchronize) flag set and an initial sequence number (seq=x). The client then enters the SYN-SENT state. **Step 2 — SYN-ACK**: The server, which was in the LISTEN state, receives the SYN and responds with a segment carrying both SYN and ACK flags. It acknowledges the client's sequence number by sending ack=x+1 and provides its own initial sequence number (seq=y). The server moves to the SYN-RECEIVED state. **Step 3 — ACK**: The client receives the SYN-ACK and sends back an ACK segment with seq=x+1 and ack=y+1. Upon sending this, the client enters the ESTABLISHED state. When the server receives the ACK, it also transitions to ESTABLISHED, and the connection is now fully open for bidirectional data transfer. Connection termination uses a four-way handshake with FIN flags, ensuring both sides agree to close gracefully. This handshake mechanism prevents duplicate or delayed packets from previous connections from interfering with new ones, a critical reliability feature of TCP.
