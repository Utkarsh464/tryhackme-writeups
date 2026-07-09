# Tasks: HTTP in Detail

## Task 1: HTTP Methods
**Purpose:** Learn the different HTTP methods and their purposes.

**Skills:** HTTP request methods.

**Theory:** GET retrieves resources without side effects. POST submits data to create resources. PUT updates/replaces resources. PATCH applies partial modifications. DELETE removes resources. OPTIONS and HEAD are also defined but less commonly used.

**Commands:** `curl -X GET http://example.com`, `curl -X POST -d "key=value" http://example.com`

---

## Task 2: HTTP Status Codes
**Purpose:** Understand the meaning of HTTP status codes.

**Skills:** Response code interpretation.

**Theory:** 1xx (Informational) — request received. 2xx (Success) — 200 OK, 201 Created. 3xx (Redirection) — 301 Moved Permanently, 302 Found. 4xx (Client Error) — 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found. 5xx (Server Error) — 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable.

**Commands:** `curl -I http://example.com` (fetch headers only to see status)

---

## Task 3: HTTP Headers
**Purpose:** Learn about request and response headers.

**Skills:** Header manipulation.

**Theory:** Request headers include Host (target domain), User-Agent (client identification), Content-Type (body format), Authorization (credentials), Cookie (session data), Referer (previous page). Response headers include Set-Cookie (store session), Content-Type, Content-Length, Location (redirect target), and Server.

**Commands:** `curl -v http://example.com`, `curl -H "User-Agent: MyAgent/1.0" http://example.com`

---

## Task 4: HTTP vs HTTPS
**Purpose:** Understand the security difference between HTTP and HTTPS.

**Skills:** TLS awareness.

**Theory:** HTTP transmits data in plaintext, making it vulnerable to eavesdropping (packet capture) and man-in-the-middle attacks. HTTPS wraps HTTP in TLS encryption, providing confidentiality, integrity, and authentication via certificates. Port 80 for HTTP, port 443 for HTTPS.

**Commands:** `curl -k https://example.com` (skip certificate verification)

---
