# Web Security Interview Questions

## 1. What are the common HTTP methods and their security implications?
**Answer:** GET (retrieve data — parameters in URL, logged in browser history, never use for sensitive data), POST (submit data — body not cached, safer than GET for forms), PUT (create/replace resource — can overwrite if not properly authorized), DELETE (remove resource — dangerous if exposed without auth), OPTIONS (reveals allowed methods — useful for reconnaissance). Security best practices: disable unnecessary methods (PUT, DELETE, TRACE), never rely on method alone for access control, and validate input regardless of method.

## 2. Explain common HTTP status codes from a security perspective.
**Answer:** Key status codes: 200 OK (success — normal operation), 301/302 (redirect — may be used for phishing), 401 Unauthorized (missing/invalid credentials), 403 Forbidden (authenticated but no permission — avoid revealing resource existence), 404 Not Found (resource missing — can be used for directory enumeration), 405 Method Not Allowed (indicates the resource exists but method is restricted), 500/502/503 (server errors — may leak stack traces or configuration details in error pages).

## 3. What is the Same-Origin Policy?
**Answer:** The Same-Origin Policy (SOP) is a critical browser security mechanism that restricts how a document or script loaded from one origin can interact with resources from another origin. Two URLs have the same origin if they share the same protocol (http/https), host (domain), and port. SOP prevents a malicious website from reading data from another site (e.g., reading email from Gmail while browsing an attacker's site). CORS and postMessage are mechanisms to relax SOP when needed.

## 4. What is SQL injection and how can it be prevented?
**Answer:** SQL injection (SQLi) occurs when user input is directly concatenated into SQL queries, allowing attackers to manipulate the query structure. Types: In-band (union-based, error-based), Inferential (blind boolean, blind time-based), and Out-of-band. Prevention: always use parameterized queries/prepared statements (not string concatenation), use an ORM with parameterized queries, validate and sanitize input, apply least privilege to database accounts, use stored procedures carefully, and employ WAFs as a defense-in-depth layer.

## 5. What are the types of XSS and how do you prevent them?
**Answer:** Cross-Site Scripting (XSS) types: (1) Reflected — payload in URL/request, reflected in response immediately (e.g., search results). (2) Stored — payload stored on server (e.g., comments, forum posts) and served to all visitors. (3) DOM-based — vulnerability in client-side JavaScript that modifies the DOM unsafely. Prevention: output encoding/escaping based on context (HTML entity, URL, JavaScript), Content Security Policy (CSP) headers, input validation, use safe frameworks (React/Vue auto-escape by default), and set HttpOnly flag on cookies.

## 6. What is CSRF and how do you prevent it?
**Answer:** Cross-Site Request Forgery (CSRF) tricks an authenticated user into performing unintended actions on a web application (e.g., changing email, transferring funds) by embedding forged requests in a malicious site. Since the user is authenticated, the server processes the request as legitimate. Prevention: CSRF tokens (unique, unpredictable values per session/request), SameSite cookies (set to Lax or Strict), custom headers (X-Requested-With), and re-authentication for sensitive actions (change password, transfer money).

## 7. How does session management work in web applications?
**Answer:** Session management maintains state for authenticated users across HTTP requests. The server creates a session (stored server-side in memory, database, or Redis) and gives the client a session identifier (session ID) in a cookie. Security best practices: use secure, HttpOnly, SameSite cookies with a cryptographically random session ID, implement session timeout (idle and absolute), regenerate session ID after login (session fixation prevention), store sessions securely server-side, and invalidate sessions on logout.

## 8. What is CORS and how does it work?
**Answer:** Cross-Origin Resource Sharing (CORS) is a browser mechanism that allows controlled access to resources from a different origin. The server specifies which origins are permitted via the `Access-Control-Allow-Origin` header. For simple requests, the browser checks the header directly. For preflighted requests (e.g., custom headers, non-standard methods), the browser sends an OPTIONS request first. Misconfigured CORS (e.g., reflecting the Origin header or using wildcard `*` with credentials) can introduce security vulnerabilities.

## 9. What is the OWASP Top 10?
**Answer:** The OWASP Top 10 is a widely recognized list of the most critical web application security risks, updated every 3-4 years. The 2021 list includes: (1) Broken Access Control, (2) Cryptographic Failures, (3) Injection (SQL, NoSQL, OS, LDAP), (4) Insecure Design, (5) Security Misconfiguration, (6) Vulnerable and Outdated Components, (7) Identification and Authentication Failures, (8) Software and Data Integrity Failures, (9) Security Logging and Monitoring Failures, (10) Server-Side Request Forgery (SSRF). It serves as an awareness document and a starting point for security programs.

## 10. What is SQL injection and how can it be prevented?
**Answer:** [Duplicate of #4 — covered above]

## 11. Explain IDOR vulnerabilities.
**Answer:** Insecure Direct Object Reference (IDOR) occurs when an application exposes internal object references (e.g., user ID, file path, database key) in URLs or parameters without proper access control. Example: `/api/user/12345` — an attacker can change the ID to access another user's data. Prevention: implement proper access control checks on every request, use indirect references (UUIDs instead of sequential IDs), and never rely on hidden parameters or obfuscation for security.

## 12. What is SSRF and why is it dangerous?
**Answer:** Server-Side Request Forgery (SSRF) occurs when an attacker can induce a server to make HTTP requests to arbitrary URLs, often to internal services. SSRF allows attackers to: scan internal networks (e.g., 169.254.169.254 for cloud metadata), access internal services (databases, admin panels, Redis), and bypass firewalls. Prevention: validate and whitelist allowed URLs/domains, block private IP ranges, disable unnecessary URL schemas (file://, gopher://), and use network segmentation.

## 13. How do you secure file uploads?
**Answer:** Secure file upload best practices: validate file type by content (magic bytes), not just extension; restrict file size; store uploads outside webroot with randomized filenames; scan for malware; serve with appropriate Content-Type headers (never user-supplied) and Content-Disposition: attachment; disable execution permissions on upload directories; validate and sanitize file names; and consider using a dedicated file storage service with built-in scanning.

## 14. What is HTTP parameter pollution?
**Answer:** HTTP Parameter Pollution (HPP) occurs when an application accepts multiple parameters with the same name, and different parts of the stack interpret them differently (e.g., PHP uses the last value, ASP.NET concatenates them). Attackers can exploit this to bypass security controls or manipulate application logic. Prevention: consistently use the first or last value, reject duplicate parameters, and perform input validation on the final parsed value, not individual occurrences.

## 15. Explain clickjacking and its mitigation.
**Answer:** Clickjacking tricks users into clicking something different from what they perceive (e.g., a hidden iframe over a legitimate button). Mitigation: set `X-Frame-Options: DENY` or `SAMEORIGIN` headers, or use Content Security Policy `frame-ancestors` directive. Both prevent your site from being loaded in iframes on other domains. For critical actions, implement confirmation dialogs or use SameSite=Strict cookies.
