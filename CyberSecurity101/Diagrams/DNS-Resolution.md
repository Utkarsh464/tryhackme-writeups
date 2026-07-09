# DNS Resolution Flow — From Browser to Authoritative Nameserver

```mermaid
sequenceDiagram
    participant User as Browser / Client
    participant Cache as Local Cache<br/>(Browser + OS)
    participant Resolver as Recursive Resolver<br/>(ISP / Public e.g. 8.8.8.8)
    participant Root as Root Nameserver
    participant TLD as TLD Nameserver<br/>(.com, .org, etc.)
    participant Auth as Authoritative Nameserver<br/>(e.g. example.com)

    User->>Cache: 1. Check local cache
    alt Cache HIT
        Cache-->>User: Return cached IP
    else Cache MISS
        Cache-->>User: Not found, query resolver
    end

    User->>Resolver: 2. Recursive query for example.com
    Resolver->>Root: 3. Query: where is .com?
    Root-->>Resolver: 4. Referral to .com TLD

    Resolver->>TLD: 5. Query: where is example.com?
    TLD-->>Resolver: 6. Referral to ns1.example.com

    Resolver->>Auth: 7. Query: IP of example.com?
    Auth-->>Resolver: 8. Answer: 93.184.216.34 (A record)

    Resolver->>User: 9. Return IP address
    User->>User: 10. Initiate HTTP connection to 93.184.216.34
```

The DNS resolution process translates human-readable domain names like `example.com` into machine-readable IP addresses. The flow begins when a user types a URL into their browser. **Step 1 — Local Cache Check**: The browser first checks its own cache, then the OS-level cache (via `nscd` or similar), and sometimes the router's DNS cache. If a cached record exists with a valid TTL, resolution ends immediately. **Step 2 — Recursive Query**: On a cache miss, the browser delegates the query to a recursive DNS resolver, usually operated by the ISP or a public resolver like Google (8.8.8.8) or Cloudflare (1.1.1.1). **Step 3-4 — Root Nameserver**: The resolver queries a root nameserver, which does not know the IP but replies with a referral to the appropriate TLD nameserver (e.g., `.com`). **Step 5-6 — TLD Nameserver**: The resolver then queries the TLD nameserver, which responds with a referral to the domain's authoritative nameserver (e.g., `ns1.example.com`). **Step 7-8 — Authoritative Nameserver**: Finally, the resolver queries the authoritative nameserver, which returns the actual A or AAAA record containing the IP address. **Step 9-10**: The resolver caches the result and returns the IP to the browser, which then initiates a TCP connection and HTTP request to that IP. DNS uses UDP port 53 by default and leverages a hierarchical, distributed database to prevent any single point of failure.
