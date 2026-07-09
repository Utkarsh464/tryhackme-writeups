# HTTP/HTTPS

## Definition
HTTP (Hypertext Transfer Protocol) is the foundation protocol for data communication on the World Wide Web. It is an application-layer protocol (Layer 7) that follows a request-response model between a client (usually a web browser) and a server. HTTPS (HTTP Secure) wraps HTTP in TLS (Transport Layer Security) encryption, providing confidentiality, integrity, and authentication.

## Why It Matters
HTTP/HTTPS is the most used protocol on the Internet. Every web application, API, and website uses it. Security professionals must understand HTTP internals to identify injection attacks, analyze web traffic, configure web application firewalls (WAFs), and conduct web penetration testing. HTTPS is the cornerstone of secure web communication — without it, all web traffic would be plaintext.

## Where It Appears in the Path
HTTP/HTTPS is introduced in the networking module and is prerequisite for most web security topics: SQL injection, XSS, OWASP Top 10, web application firewalls, and web penetration testing with tools like Burp Suite.

## Prerequisites
- TCP/IP basics (ports, connections)
- DNS (how URLs resolve to IPs)
- Familiarity with web browsing

## HTTP Methods
- **GET**: Retrieve a resource. Parameters in URL. Idempotent, cacheable.
- **POST**: Submit data (form, API payload). Changes server state. Not idempotent.
- **PUT**: Replace an entire resource at a given URL. Idempotent.
- **PATCH**: Partial modification of a resource. Not necessarily idempotent.
- **DELETE**: Remove a resource. Idempotent.
- **HEAD**: Same as GET but returns only headers (no body). Used for checking resource existence/metadata.
- **OPTIONS**: Returns allowed HTTP methods for a given URL (CORS preflight uses this).
- **CONNECT**: Establishes a tunnel (used for HTTPS proxy connections).

## HTTP Status Codes

### 1xx — Informational
- 100 Continue, 101 Switching Protocols (WebSocket upgrade)

### 2xx — Success
- 200 OK, 201 Created, 202 Accepted, 204 No Content

### 3xx — Redirection
- 301 Moved Permanently (search engines update URLs), 302 Found (temporary), 304 Not Modified (cached resources), 307/308 (preserve method on redirect)

### 4xx — Client Error
- 400 Bad Request, 401 Unauthorized (no auth), 403 Forbidden (auth but no permission), 404 Not Found, 405 Method Not Allowed, 408 Request Timeout, 429 Too Many Requests (rate limiting)

### 5xx — Server Error
- 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable, 504 Gateway Timeout

## HTTP Headers
Headers convey metadata about the request or response.

### Request Headers
- `Host`: Target domain (required in HTTP/1.1)
- `User-Agent`: Client software identification
- `Accept`: Response content types the client can parse
- `Cookie`: Session tokens stored by the browser
- `Authorization`: Credentials for Basic/Digest/Bearer auth
- `Referer`: Previous page URL (source of request)
- `Content-Type`: Format of the request body (e.g., application/json)
- `Origin`: Used in CORS — similar to Referer but always present
- `X-Forwarded-For`: Client IP when behind a proxy

### Response Headers
- `Set-Cookie`: Server instructs client to store a cookie
- `Content-Type`: Format of the response body (e.g., text/html)
- `Content-Length`: Size of response body in bytes
- `Location`: URL for redirection (3xx responses)
- `WWW-Authenticate`: Challenge for authentication
- `Cache-Control`: Caching policy (no-cache, max-age, etc.)
- `Access-Control-Allow-Origin`: CORS policy — which origins can access the resource

## HTTPS/TLS
HTTPS uses TLS (formerly SSL) to encrypt HTTP traffic. Key components:
- **TLS Handshake**: Client and server negotiate cipher suites, exchange certificates (X.509), derive session keys, and establish an encrypted connection.
- **Certificate Authority (CA)**: Trusted third-party that issues digital certificates verifying server identity.
- **Certificate Validation**: Client checks certificate chain, expiry, revocation (CRL/OCSP), and hostname match.
- **Forward Secrecy**: Ephemeral key exchange (ECDHE) ensures past sessions can't be decrypted if the private key is compromised.
- **TLS Versions**: SSLv2/SLLv3 (insecure, deprecated) → TLS 1.0 (deprecated) → TLS 1.1 (deprecated) → TLS 1.2 (current standard) → TLS 1.3 (improved security and performance).

## Common Interview Questions
1. **What is the difference between HTTP and HTTPS?** HTTPS encrypts HTTP traffic using TLS, providing confidentiality, integrity, and authentication. HTTP is plaintext and vulnerable to interception.
2. **Explain the difference between GET and POST.** GET appends data to the URL (visible, cached, length-limited), used for retrieval. POST sends data in the body (not cached, no length limit), used for state-changing operations.
3. **What is a 401 vs 403 status code?** 401 Unauthorized = no authentication provided. 403 Forbidden = authenticated but lacks permission.
4. **What is HTTP Strict Transport Security (HSTS)?** A header that forces browsers to only connect via HTTPS, preventing downgrade attacks. Includes `max-age`, `includeSubDomains`, and `preload` directives.
5. **How does TLS 1.3 differ from TLS 1.2?** TLS 1.3 removes insecure cipher suites, reduces handshake to 1 round trip (0-RTT for resumed sessions), removes static RSA key exchange, and simplifies the protocol.
6. **What is a man-in-the-middle (MITM) attack on HTTPS?** Intercepting HTTPS traffic by installing a fake CA certificate on the victim's device (e.g., corporate proxies, malware). The browser shows a warning if the CA is not trusted.

## Further Reading
- [RFC 7230-7235 — HTTP/1.1](https://tools.ietf.org/html/rfc7230)
- [RFC 8446 — TLS 1.3](https://tools.ietf.org/html/rfc8446)
- [Mozilla Observatory](https://observatory.mozilla.org/) (test HTTPS configuration)
- [OWASP Transport Layer Protection Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Transport_Layer_Protection_Cheat_Sheet.html)
- [HTTP Cat](https://http.cat/) (visual status code reference)
