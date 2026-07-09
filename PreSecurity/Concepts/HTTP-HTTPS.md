# HTTP / HTTPS

## Definition
Hypertext Transfer Protocol (HTTP) is an application-layer protocol for distributed, hypermedia systems—the foundation of data communication on the web. HTTPS adds TLS encryption on top of HTTP. HTTP methods include GET, POST, PUT, DELETE, PATCH, and HEAD. Status codes are grouped: 1xx (informational), 2xx (success), 3xx (redirection), 4xx (client error), 5xx (server error).

## Why It Matters
HTTP is the most attacked protocol on the internet. Web application security relies on understanding request/response structure, headers (Cookies, CORS, Content-Security-Policy), and statelessness. Injection attacks, CSRF, XSS, and session hijacking all exploit HTTP semantics.

## Where It Appears in the Path
- How The Web Works
- Web Hacking Fundamentals

## Prerequisites
- Networking basics, DNS

## Key Points
- HTTP is stateless; sessions use cookies/tokens
- HTTPS uses TLS handshake (certificate exchange, key agreement)
- Common headers: Host, User-Agent, Content-Type, Authorization
- Status code categories: 2xx OK, 3xx redirect, 4xx client error, 5xx server error

## Common Interview Questions
1. What is the difference between HTTP and HTTPS?
**Answer:** HTTPS encrypts HTTP traffic using TLS/SSL.
2. What does a 403 status code mean?
**Answer:** Forbidden — the server understood the request but refuses to authorize it.
3. What is HSTS?
**Answer:** HTTP Strict Transport Security — a header that forces browsers to use HTTPS only.

## Further Reading
- RFC 7230–7235 (HTTP/1.1)
- MDN HTTP Guide
- OWASP Transport Layer Protection