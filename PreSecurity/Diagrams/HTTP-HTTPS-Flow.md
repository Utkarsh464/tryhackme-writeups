# HTTP/HTTPS Flow

```mermaid
sequenceDiagram
    participant Client
    participant Server

    Note over Client,Server: TLS Handshake (HTTPS only)
    Client->>Server: ClientHello (cipher suites, TLS version)
    Server->>Client: ServerHello (selected cipher, certificate)
    Client->>Server: Key Exchange
    Client->>Server: Finished (encrypted)
    Server->>Client: Finished (encrypted)
    Note over Client,Server: Secure Channel Established
    Client->>Server: HTTP Request (GET /index.html)
    Server-->>Client: HTTP Response (200 OK, Content)
    Client->>Server: HTTP Request (POST /login, data)
    Server-->>Client: HTTP Response (302 Redirect, Set-Cookie)
    Client->>Server: HTTP Request (GET /dashboard, Cookie)
    Server-->>Client: HTTP Response (200 OK, Dashboard HTML)
```

HTTPS requests begin with a TLS handshake to establish an encrypted tunnel, followed by standard HTTP request/response exchanges. Under HTTP, the same request/response pattern occurs without encryption, leaving data vulnerable to interception.
