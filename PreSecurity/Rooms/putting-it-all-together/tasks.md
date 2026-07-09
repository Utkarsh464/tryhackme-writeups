# Tasks: Putting It All Together

## Task 1: URL Entry and DNS Resolution
**Purpose:** Understand what happens when a URL is typed into a browser.

**Skills:** Full request lifecycle step 1.

**Theory:** The browser first checks its cache for the domain's IP, then the OS cache, and finally the router cache. If none exist, a recursive DNS query is made. The DNS resolver contacts root, TLD, and authoritative servers to obtain the IP address.

**Commands:** `dig +trace tryhackme.com`

---

## Task 2: TCP and TLS Handshakes
**Purpose:** Learn how connections are established securely.

**Skills:** Full request lifecycle steps 2-3.

**Theory:** A TCP three-way handshake (SYN, SYN-ACK, ACK) establishes a connection with the server. For HTTPS, a TLS handshake follows: the client sends a ClientHello, the server responds with its certificate and cipher choice, key exchange occurs, and encrypted communication begins.

**Commands:** N/A

---

## Task 3: HTTP Request and Response
**Purpose:** Understand the HTTP request/response exchange.

**Skills:** Full request lifecycle steps 4-5.

**Theory:** The browser sends an HTTP request including the method (GET), path, HTTP version, and headers (Host, User-Agent, Accept). The server processes the request and returns an HTTP response with a status code (e.g., 200 OK), headers (Content-Type, Content-Length), and the response body (HTML).

**Commands:** `curl -v https://tryhackme.com`

---

## Task 4: Browser Rendering
**Purpose:** Learn how the browser renders the page.

**Skills:** Full request lifecycle step 6.

**Theory:** The browser parses HTML to build the DOM tree, CSS to build the CSSOM (CSS Object Model), and combines them into the render tree. JavaScript is executed (blocking parsing unless async/deferred). Additional resources (images, CSS, JS) trigger further HTTP requests. The final page is painted to the screen.

**Commands:** N/A

---

## Task 5: Security Implications
**Purpose:** Identify security issues at each stage.

**Skills:** Web security awareness.

**Theory:** At DNS: spoofing/cache poisoning. At TCP: SYN floods. At TLS: certificate validation failures, obsolete cipher suites. At HTTP: header injection, insecure cookies. At server: SQL injection, command injection. At rendering: XSS, content injection via unsafe innerHTML.

**Commands:** N/A

---
