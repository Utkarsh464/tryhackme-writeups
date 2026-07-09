# Concepts: Putting It All Together

## 1. Full Request Lifecycle
When a user types a URL and presses Enter, six main phases occur: (1) DNS resolution, (2) TCP handshake, (3) TLS handshake (for HTTPS), (4) HTTP request, (5) server processing and response, (6) browser rendering. Each phase presents unique security considerations.

## 2. DNS Resolution in the Lifecycle
The browser checks multiple caches (browser, OS, router) before making a recursive DNS query. The time-to-live (TTL) on DNS records determines how long they are cached. If the DNS response is poisoned, the browser connects to a malicious IP — this is DNS spoofing.

## 3. TCP Three-Way Handshake
Before data can be exchanged, the client and server synchronize via SYN → SYN-ACK → ACK. This establishes a reliable connection with sequenced data delivery. Security concern: SYN flood attacks exhaust server resources by sending SYN packets without completing the handshake.

## 4. TLS Handshake
The TLS handshake adds encryption to the connection. The client sends supported cipher suites. The server selects one and sends its certificate (signed by a Certificate Authority). A key exchange generates session keys. After the handshake, all data is encrypted. Weak ciphers and expired certificates are security risks.

## 5. HTTP Request
The browser builds an HTTP request with a method (GET for page loads), path (e.g., `/`), HTTP version (usually HTTP/2 or HTTP/1.1), and headers. The Host header is mandatory for virtual hosting. Security considerations: sensitive data in URL parameters (exposed in logs, referer headers).

## 6. Server Processing
The web server receives the request and determines how to respond. Static files are served directly. Dynamic content may involve databases, application servers, or APIs. Common vulnerabilities at this stage include SQL injection, command injection, path traversal, and insecure deserialization.

## 7. HTTP Response
The server returns a response with a status code and headers. The Content-Type header tells the browser how to interpret the body (text/html, application/json). Security headers like Content-Security-Policy, X-Frame-Options, and Strict-Transport-Security protect against various attacks.

## 8. Browser Rendering
The browser parses HTML into the DOM tree. When it encounters `<script>` tags (without async/defer), parsing pauses until the script executes. CSS is parsed into CSSOM. The render tree combines DOM and CSSOM, then layout computes positions, and painting renders pixels. Additional resources trigger more HTTP requests.
