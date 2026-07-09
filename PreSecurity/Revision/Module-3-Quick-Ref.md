# Module 3: How The Web Works — Quick Reference

## Key Concepts
- **DNS Records**: A (IPv4), AAAA (IPv6), CNAME (alias), MX (mail), TXT (text), NS (nameserver)
- **HTTP Methods**: GET (read), POST (create), PUT (update/replace), DELETE (remove), PATCH (partial update)
- **HTTP Status Codes**: 2xx Success, 3xx Redirection, 4xx Client Error, 5xx Server Error
- **Cookies**: Session identifiers stored by browser, sent with requests
- **Sessions**: Server-side state linked to a session ID stored in a cookie
- **HTML Structure**: `<!DOCTYPE html>` → `<html>` → `<head>` (metadata) + `<body>` (content)
- **JavaScript**: Client-side scripting for dynamic web behavior
- **Request Lifecycle**: URL entry → DNS lookup → TCP handshake → TLS handshake (HTTPS) → HTTP request → server processes → HTTP response → browser renders

## Important Commands
| Command | Purpose |
|---------|---------|
| `curl URL` | Make HTTP requests from CLI |
| `curl -v URL` | Verbose output with headers |
| `curl -X POST -d "data" URL` | Send POST request |
| `curl -H "Header: value" URL` | Add custom header |
| `ping domain` | Check connectivity |
| `nslookup domain` | DNS lookup |
| `dig domain` | Detailed DNS query |

## Key Terms
- **Client**: Browser or application making requests
- **Server**: Computer hosting websites/services
- **CDN**: Content Delivery Network — caches content geographically
- **WAF**: Web Application Firewall — filters malicious HTTP traffic
- **Load Balancer**: Distributes traffic across multiple servers
- **REST**: REpresentational State Transfer — API architectural style
- **AJAX**: Async JavaScript — updates page without full reload
- **JSON**: JavaScript Object Notation — common data format for APIs
