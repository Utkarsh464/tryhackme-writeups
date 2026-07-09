# HTTP Request/Response Cycle and HTTPS/TLS Handshake

```mermaid
sequenceDiagram
    participant Client as Client (Browser)
    participant Server as Web Server

    Note over Client,Server: HTTP (Unencrypted)
    Client->>Server: 1. TCP 3-Way Handshake (SYN, SYN-ACK, ACK)
    Client->>Server: 2. HTTP Request (GET /index.html HTTP/1.1)
    Note over Client: Headers: Host, User-Agent, Accept, Cookie
    Server-->>Client: 3. HTTP Response (200 OK)
    Note over Server: Headers: Content-Type, Set-Cookie, Cache-Control
    Server-->>Client: 4. Response Body (HTML, JSON, etc.)
    Client->>Client: 5. Render page / Execute JS / Load resources

    Note over Client,Server: HTTPS (TLS Encrypted)
    Client->>Server: 6. TCP 3-Way Handshake
    Note over Client,Server: TLS Handshake Begins
    Client->>Server: 7. ClientHello (TLS version, cipher suites, random bytes)
    Server-->>Client: 8. ServerHello (chosen cipher, session ID, cert)
    Server-->>Client: 9. Certificate (X.509 public key cert)
    Server-->>Client: 10. ServerHelloDone
    Client->>Client: 11. Verify certificate (CA chain, expiration, hostname)
    Client->>Server: 12. ClientKeyExchange (pre-master secret encrypted with public key)
    Client->>Server: 13. ChangeCipherSpec + Finished (encrypted handshake hash)
    Server-->>Client: 14. ChangeCipherSpec + Finished
    Note over Client,Server: TLS Tunnel Established — Symmetric Keys In Use
    Client->>Server: 15. Encrypted HTTP Request
    Server-->>Client: 16. Encrypted HTTP Response
```

The HTTP protocol follows a simple request-response model between a client (browser) and a server. In standard **HTTP**, after the TCP three-way handshake completes, the client sends an HTTP request containing a method (GET, POST, etc.), a URI, headers, and optionally a body. The server processes the request and responds with a status line (e.g., 200 OK, 404 Not Found), headers, and the requested content. The connection may be kept alive for subsequent requests (HTTP/1.1 Keep-Alive) or multiplexed (HTTP/2). **HTTPS** adds the TLS (Transport Layer Security) layer on top of TCP. The TLS handshake begins with the **ClientHello**, where the browser advertises supported TLS versions and cipher suites. The server responds with a **ServerHello** choosing the strongest common cipher, plus its X.509 digital certificate containing the public key. The client validates the certificate against a trusted Certificate Authority (CA) chain, checks expiration, and verifies the hostname. The client then generates a pre-master secret, encrypts it with the server's public key, and sends it back. Both sides derive symmetric session keys from this secret. **ChangeCipherSpec** messages signal the switch to encrypted communication, and the handshake is verified with an encrypted Finished message. All subsequent HTTP data is encrypted with the symmetric session keys, providing confidentiality, integrity, and server authentication.
