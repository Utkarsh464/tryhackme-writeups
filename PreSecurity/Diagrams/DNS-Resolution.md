# DNS Resolution

```mermaid
sequenceDiagram
    participant Client as Client Browser
    participant Recursive as Recursive Resolver
    participant Root as Root Nameserver
    participant TLD as TLD Nameserver
    participant Authoritative as Authoritative Nameserver

    Client->>Recursive: Query: example.com?
    Recursive->>Root: Where is .com TLD?
    Root-->>Recursive: .com TLD server IP
    Recursive->>TLD: Where is example.com?
    TLD-->>Recursive: Authoritative server for example.com
    Recursive->>Authoritative: What is IP of example.com?
    Authoritative-->>Recursive: 93.184.216.34
    Recursive-->>Client: 93.184.216.34
    Note over Client,Authoritative: Client caches result and connects to 93.184.216.34
```

DNS resolution translates human-readable domain names into IP addresses. The client's recursive resolver queries a hierarchy of nameservers—root, TLD (Top-Level Domain), and authoritative—to find the correct IP address, with caching at each level to improve performance.
