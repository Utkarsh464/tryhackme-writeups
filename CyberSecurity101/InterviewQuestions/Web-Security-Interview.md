# Web Security Interview Questions & Answers

## 1. Explain the OWASP Top 10 (2021).

**Answer:** OWASP Top 10 lists the most critical web application security risks: 1) Broken Access Control - users accessing unauthorized resources (IDOR, privilege escalation). 2) Cryptographic Failures - weak encryption, exposed sensitive data. 3) Injection - SQL, NoSQL, OS, LDAP injection. 4) Insecure Design - missing security controls in architecture. 5) Security Misconfiguration - default credentials, unnecessary features, directory listing. 6) Vulnerable/Outdated Components - using known-vulnerable libraries (Log4j, etc.). 7) Identification/Authentication Failures - weak passwords, session fixation. 8) Software/Data Integrity Failures - CI/CD pipeline attacks, unsigned updates. 9) Security Logging/Monitoring Failures - insufficient incident detection. 10) SSRF (Server-Side Request Forgery) - server making unintended requests.

## 2. What is SQL injection and how do you prevent it?

**Answer:** SQL injection occurs when user input is embedded directly into SQL queries without sanitization. Types: In-band (error-based, UNION-based - results in HTTP response), Blind (boolean-based - true/false responses, time-based - delays), Out-of-band (DNS/HTTP exfiltration). Example: `' OR 1=1--` bypasses authentication. Prevention: 1) Parameterized queries/prepared statements (strongest defense). 2) Stored procedures. 3) Input validation (whitelist over blacklist). 4) Least privilege for DB accounts. 5) ORM frameworks (but can be vulnerable to NoSQL injection). 6) WAF rules. 7) Escape special characters. Never concatenate user input directly into queries.

## 3. Explain Cross-Site Scripting (XSS) types and mitigation.

**Answer:** XSS injects malicious scripts into web pages viewed by other users. Types: 1) Stored/Persistent - script stored on server (comments, profiles). 2) Reflected - script in URL/request, reflected in response immediately (phishing links). 3) DOM-based - vulnerability in client-side JavaScript, not server response. Payload examples: `<script>alert('XSS')</script>`, `<img src=x onerror=alert(1)>`, `<svg onload=alert(1)>`. Impact: session hijacking (stealing cookies), keylogging, phishing, defacement, CSRF token theft. Prevention: 1) Output encoding/escaping (context-aware: HTML, JS, CSS, URL). 2) Content Security Policy (CSP) headers. 3) HttpOnly cookies (prevent JS access). 4) Input validation. 5) Sanitization libraries (DOMPurify).

## 4. How does session management work and what are common vulnerabilities?

**Answer:** After authentication, the server creates a session (stored server-side) and sends a session ID to the client via cookie or URL. The client sends the session ID with each request for state tracking. Vulnerabilities: 1) Session fixation - attacker sets victim's session ID before login. 2) Session prediction - weak session ID generation (predictable). 3) Session hijacking - stealing session ID via XSS, network sniffing, or MITM. 4) Weak session timeout - sessions never expire. 5) Concurrent session issues. Prevention: Generate random session IDs, use HttpOnly/Secure/SameSite flags, implement proper timeout, regenerate ID after login, use HTTPS, bind session to IP/User-Agent.

## 5. Explain Cross-Site Request Forgery (CSRF).

**Answer:** CSRF tricks an authenticated user into making unintended requests. Example: Victim visits attacker's page while logged into bank.com. Attacker's page contains `<img src="bank.com/transfer?amount=1000&to=attacker">`. Browser automatically sends cookies, making the request appear legitimate. The server can't distinguish legitimate requests from forged ones. Prevention: 1) CSRF tokens (unique, unpredictable tokens in forms, validated server-side). 2) SameSite cookies (Strict/Lax mode). 3) Custom request headers (X-Requested-With). 4) Double-submit cookies. 5) Re-authentication for sensitive actions. 6) CAPTCHA for critical operations. 7) Check Origin/Referer headers.

## 6. What is authentication and authorization? How are they different?

**Answer:** Authentication verifies identity ("Who are you?") - typically via passwords, biometrics, MFA, SSO. Authorization determines what an authenticated user can access ("What are you allowed to do?") - enforced via RBAC, ABAC, ACLs. Common failures: Weak password policies, credential stuffing, lack of MFA, insecure password recovery, exposed session IDs, JWTs without proper validation. Best practices: bcrypt/argon2 for password hashing, rate limiting (fail2ban), account lockout, MFA, OAuth 2.0/OpenID Connect for federated auth, principle of least privilege. Never roll your own authentication system.

## 7. Explain JWT (JSON Web Tokens) and its security considerations.

**Answer:** JWT is a compact, self-contained token format for transmitting claims between parties. Structure: header (algorithm, type), payload (claims like sub, exp, iat), signature (header+payload signed with secret). Tokens are base64url-encoded, NOT encrypted by default. Security considerations: 1) Algorithm confusion attack - change alg from RS256 to HS256 to use public key as HMAC secret. 2) "none" algorithm attack - set alg to none, bypass signature verification. 3) Weak secret key for HS256 (brute-forceable). 4) Token not expired (no exp validation). 5) Sensitive data in payload (base64 is not encryption). 6) Token theft via XSS. 7) Insufficient token length (should be minimum 256-bit symmetric key or 2048-bit RSA). Prevention: Use strong algorithms, validate all claims, use short expiration, implement token rotation, store securely (HttpOnly cookies not localStorage for SPAs).

## 8. What is IDOR (Insecure Direct Object Reference)?

**Answer:** IDOR is a broken access control vulnerability where user-supplied input (like IDs, filenames, keys) is used to access resources without proper authorization checks. Example: `GET /api/user/12345/profile` - changing 12345 to 12346 accesses another user's data. Other examples: `/download?file=report.pdf` changed to `download?file=../../etc/passwd` (path traversal). Prevention: Implement proper authorization checks for every resource access, use indirect references (UUIDs, random IDs), verify ownership, don't expose internal IDs unnecessarily, use attribute-based access control.

## 9. Explain Server-Side Request Forgery (SSRF).

**Answer:** SSRF forces the server to make requests to unintended locations. The attacker manipulates URL parameters to make the server request internal resources. Types: Basic (response returned to attacker), Blind (no direct response, but side effects). Impact: Access internal services (cloud metadata endpoints like 169.254.169.254), read local files (file:///), port scan internal network, bypass firewalls, interact with internal APIs. Prevention: 1) Whitelist allowed URLs/domains. 2) Block private IP ranges (127.0.0.0/8, 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16, 169.254.0.0/16). 3) Disable unnecessary URL schemes (file://, gopher://). 4) Use DNS resolution validation. 5) Network segmentation. 6) Strict input validation.

## 10. How do you protect sensitive data at rest and in transit?

**Answer:** At rest: Encrypt databases (TDE), encrypt files (AES-256), use encrypted filesystems (LUKS), secure key management (HSM, KMS). For passwords: use strong adaptive hashing (bcrypt, argon2, scrypt) with salt. For credit cards: tokenization or format-preserving encryption. Don't store what you don't need. In transit: TLS 1.2+ with strong ciphers (TLS_AES_256_GCM), HSTS headers, certificate pinning (or certificate transparency), disable old protocols (SSLv3, TLS 1.0/1.1). SSH for remote access. Avoid sending sensitive data in URLs (they're logged). Use secure coding practices to avoid leakage in error messages, logs, or API responses.

## 11. Explain Content Security Policy (CSP).

**Answer:** CSP is a browser security mechanism that mitigates XSS and data injection attacks. Implemented via `Content-Security-Policy` HTTP header. Directives control allowed sources for resources: `default-src` (fallback), `script-src` (JavaScript), `style-src` (CSS), `img-src` (images), `connect-src` (XHR/fetch), `frame-src` (iframes), `object-src` (plugins). Example: `Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.example.com; img-src *`. Nonce-based CSP: `script-src 'nonce-rAnd0m'`. Strict CSP uses hashes. Report-URI/report-to collects violations. Pitfalls: inline styles/scripts are blocked without 'unsafe-inline', eval() is blocked without 'unsafe-eval'.

## 12. What is CORS and how does it work?

**Answer:** CORS (Cross-Origin Resource Sharing) controls which origins can access resources from a different origin. Browsers enforce same-origin policy by default - scripts from `example.com` can't read responses from `api.example.org`. CORS uses HTTP headers: `Access-Control-Allow-Origin` (which origins are allowed, can be `*` or specific), `Access-Control-Allow-Methods`, `Access-Control-Allow-Headers`, `Access-Control-Allow-Credentials`. Preflight requests (OPTIONS) are sent for non-simple requests (custom headers, non-standard methods). Security issues: overly permissive CORS (`*` with credentials), reflecting origin header without validation, trusting arbitrary origins.

## 13. Explain the difference between authentication vulnerabilities and authorization vulnerabilities.

**Answer:** Authentication vulnerabilities: weak passwords, no MFA, credential stuffing acceptance, insecure password reset (token in URL/logs), user enumeration (different error messages for valid vs invalid users), session management flaws (predictable tokens, no timeout, missing regeneration). Authorization vulnerabilities: IDOR (direct object reference), privilege escalation (horizontal - access same-role user data, vertical - access admin functions), missing function-level access control, path traversal, forced browsing. Authentication flaws let attackers impersonate users; authorization flaws let authenticated users access what they shouldn't. Both must be tested thoroughly.

## 14. What is XXE (XML External Entity) injection?

**Answer:** XXE exploits XML parsers that process external entities. Attackers define entities that reference external resources. Types: In-band (data returned in response), Blind (OOB - out-of-band exfiltration via HTTP/DNS). Payload: `<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd">]> <root>&xxe;</root>`. Impact: Reading local files, SSRF to internal systems, denial of service (Billion Laughs attack), port scanning. Prevention: Disable external entity processing in XML parsers (most important), use less complex data formats (JSON), patch XML libraries, implement input validation. In Java: `DocumentBuilderFactory.setFeature("http://apache.org/xml/features/disallow-doctype-decl", true)`.

## 15. How do you implement secure file upload functionality?

**Answer:** File uploads are high-risk. Secure implementation: 1) Validate file type via content inspection (magic bytes), not just extension. 2) Restrict allowed types (whitelist). 3) Validate file size (limit max size). 4) Store files outside webroot. 5) Use randomized filenames (UUID, not user-supplied name). 6) Scan for malware. 7) Serve files with Content-Disposition: attachment (prevent execution). 8) Disable execution permissions on upload directory. 9) Check image recompression for image uploads. 10) Anti-virus scanning. Attacks: RCE via uploaded PHP/JSP shell, XSS via SVG with embedded JS, ZIP bombs, path traversal in filename (../../../etc/cronjob).

## 16. Explain HTTP request smuggling.

**Answer:** HTTP request smuggling exploits discrepancies between how front-end (proxy/load balancer) and back-end servers parse HTTP requests, especially Content-Length vs Transfer-Encoding headers. Types: CL.TE (front-end uses Content-Length, back-end uses Transfer-Encoding), TE.CL, TE.TE (malformed TE headers). Impact: Cache poisoning (serve attacker's response to other users), session hijacking, bypassing security controls, WAF evasion. Prevention: Reject ambiguous requests, use HTTP/2 (eliminates ambiguity), standardize parsing across servers, normalize headers at the front-end, disable HTTP keep-alive if not needed.

## 17. What is the difference between stored, reflected, and DOM-based XSS?

**Answer:** Stored XSS: The malicious script is permanently stored on the server (database, comment system, forum). Every user viewing the page gets attacked. Highest impact. Reflected XSS: The script is embedded in the current request (URL parameter, form input) and reflected back immediately. Requires user interaction (clicking crafted link). DOM-based XSS: The vulnerability exists entirely in client-side JavaScript. The server is never involved in the injection. The attack payload modifies the DOM environment. Detection requires analyzing JavaScript code flow. Example: `document.write(location.hash.substring(1))` - attacker controls URL fragment.

## 18. Explain WebSocket security considerations.

**Answer:** WebSockets provide full-duplex communication over a single TCP connection. Security: 1) Use `wss://` (WebSocket Secure over TLS) not `ws://`. 2) Origin header validation (but can be spoofed). 3) Authentication should happen at the application layer (not just at upgrade request). 4) No CSRF protection built-in - implement token-based auth in messages. 5) Input validation on all messages (server-side). 6) Rate limiting to prevent abuse. 7) Message size limits. 8) Close idle connections. WebSockets bypass traditional HTTP security controls (WAFs may not inspect WebSocket frames).

## 19. What is the Same-Origin Policy and why is it important?

**Answer:** The Same-Origin Policy (SOP) is a critical browser security mechanism that restricts how documents/scripts from one origin can interact with resources from another origin. Origin = scheme (http/https) + host (domain) + port. Two URLs with different origins are considered cross-origin. SOP prevents malicious sites from reading data from other sites (e.g., reading banking emails). Exceptions: `<script>`, `<img>`, `<link>`, `<iframe>` tags can embed cross-origin resources (read is restricted though). CORS relaxes SOP for legitimate cross-origin requests. Without SOP, any website could read your email, bank balance, etc.

## 20. How do you securely store API keys and secrets?

**Answer:** Never hardcode secrets in source code (committed to git). Best practices: 1) Environment variables (not in .env committed to repo). 2) Secret management services (HashiCorp Vault, AWS Secrets Manager, Azure Key Vault). 3) Encrypted config files with key management. 4) Use CI/CD secrets (GitHub Actions secrets, GitLab CI variables). 5) Regular secret rotation. 6) Access control - least privilege for secrets. 7) Audit logging of secret access. 8) Use .gitignore for secret files. 9) Scan repos for accidental commits (git-secrets, truffleHog). 10) Don't log secrets. 11) For client-side apps, use backend proxy or PKCE flow.

## 21. What is Race Condition in web applications?

**Answer:** A race condition occurs when multiple threads/processes access shared resources simultaneously without proper synchronization, leading to unexpected behavior. In web apps: Time-of-check to time-of-use (TOCTOU) - checking permissions before an operation, then the state changes before the operation executes. Examples: Coupon code reuse (multiple requests before code is marked used), bank transfer race conditions, file upload races. Prevention: Use database transactions with proper isolation levels, optimistic/pessimistic locking, atomic operations, mutexes/semaphores, idempotency keys for critical operations.

## 22. Explain GraphQL security considerations.

**Answer:** GraphQL APIs expose a single endpoint and let clients query exactly what they need. Security issues: 1) Information disclosure via introspection (disable in production or restrict). 2) Deeply nested queries (billion laughs attack) - implement query depth limits. 3) Rate limiting at query complexity level (not just request count). 4) Authorization checks at the field level, not just endpoint level. 5) Batch attacks (multiple operations in single request). 6) N+1 query problem can be exploited for DoS. Defenses: Use query complexity analysis, depth limiting, timeouts, field-level authorization, disable introspection in prod, use persisted queries.

## 23. What are HTTP security headers and which ones are important?

**Answer:** Key security headers: 1) `Strict-Transport-Security` (HSTS) - forces HTTPS, prevents SSL stripping. 2) `Content-Security-Policy` (CSP) - mitigates XSS and data injection. 3) `X-Content-Type-Options: nosniff` - prevents MIME type sniffing. 4) `X-Frame-Options: DENY/SAMEORIGIN` - prevents clickjacking. 5) `X-XSS-Protection` - legacy, mostly obsolete. 6) `Referrer-Policy` - controls referrer header leakage. 7) `Permissions-Policy` (formerly Feature-Policy) - controls browser features (camera, mic, geolocation). 8) `Set-Cookie` with SameSite, HttpOnly, Secure flags. 9) `Access-Control-Allow-Origin` for CORS. Missing headers are common findings in security assessments.

## 24. How do you perform a web application security assessment?

**Answer:** Methodology: 1) Reconnaissance - gather information (subdomains, endpoints, technologies via tools like subfinder, httpx, whatweb). 2) Mapping - spider/crawl application, identify attack surface, map functionality. 3) Authentication testing - test for weaknesses (credential stuffing, weak policies, session flaws). 4) Input validation testing - SQLi, XSS, SSTI, command injection, XXE, LFI/RFI. 5) Business logic testing - understand workflow, test for logic flaws, race conditions. 6) Authorization testing - IDOR, privilege escalation tests. 7) Configuration testing - default creds, directory listing, exposed admin panels. 8) Reporting - document findings with POC, risk rating, remediation. Tools: Burp Suite (Professional for active scan), OWASP ZAP, Nuclei, custom scripts.

## 25. What is the difference between black-box, white-box, and gray-box testing?

**Answer:** Black-box testing: Tester has no internal knowledge of the application. Simulates an external attacker. Tests from the outside in. Advantages: realistic attacker perspective, unbiased. Disadvantages: may miss vulnerabilities requiring source code analysis. White-box testing: Tester has full access to source code, architecture docs, credentials. Code review for vulnerabilities, static analysis. Advantages: thorough coverage, finds logic flaws and backdoors. Disadvantages: time-consuming, may miss runtime/environment issues. Gray-box testing: Tester has partial knowledge (credentials, API docs, but not full source). Most common real-world scenario: authenticated testing simulates an insider or attacker with some access.
