# Web Security Cheat Sheet

## HTTP Methods
| Method | Description | Safe | Idempotent |
|--------|-------------|------|------------|
| `GET` | Retrieve resource | Yes | Yes |
| `HEAD` | Headers only | Yes | Yes |
| `POST` | Create resource | No | No |
| `PUT` | Replace resource | No | Yes |
| `PATCH` | Partial update | No | No |
| `DELETE` | Remove resource | No | Yes |
| `OPTIONS` | Available methods | Yes | Yes |
| `TRACE` | Diagnostic echo | Yes | Yes |
| `CONNECT` | Tunnel proxy | No | No |

## HTTP Status Codes
| Code | Category | Examples |
|------|----------|---------|
| 1xx | Informational | 101 Switching Protocols |
| 200 | OK | Success |
| 201 | Created | Resource created |
| 204 | No Content | Delete success |
| 301 | Moved Permanently | Permanent redirect |
| 302 | Found | Temporary redirect |
| 304 | Not Modified | Cached version |
| 400 | Bad Request | Malformed request |
| 401 | Unauthorized | Login required |
| 403 | Forbidden | Access denied |
| 404 | Not Found | Resource missing |
| 405 | Method Not Allowed | Wrong method |
| 429 | Too Many Requests | Rate limited |
| 500 | Internal Server Error | Server error |
| 502 | Bad Gateway | Upstream failed |
| 503 | Service Unavailable | Overloaded |
| 504 | Gateway Timeout | Upstream timeout |

## Common HTTP Headers
### Request Headers
| Header | Example |
|--------|---------|
| `Host` | `Host: example.com` |
| `User-Agent` | `User-Agent: Mozilla/5.0 ...` |
| `Referer` | `Referer: https://example.com/login` |
| `Authorization` | `Authorization: Bearer <token>` |
| `Cookie` | `Cookie: session=abc123` |
| `Content-Type` | `Content-Type: application/json` |
| `Content-Length` | `Content-Length: 42` |
| `Origin` | `Origin: https://example.com` |
| `X-Forwarded-For` | `X-Forwarded-For: 127.0.0.1` |

### Response Headers
| Header | Purpose |
|--------|---------|
| `Set-Cookie` | Set cookie |
| `Location` | Redirect URL |
| `Content-Type` | Response format |
| `Content-Length` | Response size |
| `Server` | Server info |
| `X-Powered-By` | Technology info |
| `WWW-Authenticate` | Auth challenge |
| `Access-Control-Allow-Origin` | CORS policy |
| `Strict-Transport-Security` | HSTS |

## Security Headers
| Header | Syntax | Purpose |
|--------|--------|---------|
| `Content-Security-Policy` | `default-src 'self'` | XSS prevention |
| `X-Frame-Options` | `DENY` | Clickjacking |
| `X-Content-Type-Options` | `nosniff` | MIME sniffing |
| `Strict-Transport-Security` | `max-age=31536000` | Force HTTPS |
| `X-XSS-Protection` | `1; mode=block` | XSS filter |
| `Referrer-Policy` | `no-referrer` | Referrer info |
| `Permissions-Policy` | `geolocation=()` | Feature control |
| `Cache-Control` | `no-store` | Caching control |
| `Access-Control-Allow-Origin` | `https://example.com` | CORS |

## CSP Directives
| Directive | Example |
|-----------|---------|
| `default-src` | `default-src 'self'` |
| `script-src` | `script-src 'self' https://cdn.jsdelivr.net` |
| `style-src` | `style-src 'self' 'unsafe-inline'` |
| `img-src` | `img-src 'self' data:` |
| `connect-src` | `connect-src 'self' api.example.com` |
| `font-src` | `font-src fonts.gstatic.com` |
| `frame-src` | `frame-src 'none'` |
| `object-src` | `object-src 'none'` |
| `base-uri` | `base-uri 'self'` |
| `report-uri` | `report-uri /csp-report` |

## CORS Configurations
| Configuration | Access |
|---------------|--------|
| `Access-Control-Allow-Origin: *` | All domains (dangerous) |
| `Access-Control-Allow-Origin: https://trusted.com` | Specific domain |
| `Access-Control-Allow-Credentials: true` | Allow cookies |
| `Access-Control-Allow-Methods: GET,POST` | Allowed methods |
| `Access-Control-Allow-Headers: Content-Type` | Allowed headers |
| `Access-Control-Max-Age: 3600` | Preflight cache |
| `Vary: Origin` | Dynamic origin |

## OWASP Top 10 (2021)
| Rank | Category |
|------|----------|
| A01 | Broken Access Control |
| A02 | Cryptographic Failures |
| A03 | Injection |
| A04 | Insecure Design |
| A05 | Security Misconfiguration |
| A06 | Vulnerable Components |
| A07 | Auth Failures |
| A08 | Data Integrity Failures |
| A09 | Logging/Monitoring |
| A10 | SSRF |

## Common Security Checks
```bash
# Check security headers
curl -sI https://example.com | grep -iE "strict-transport|content-security|x-frame|x-content|x-xss|referrer"

# Test for HTTP methods
curl -X OPTIONS https://example.com -I

# Check for directory listing
curl https://example.com/uploads/

# Test for open redirect
curl -I "https://example.com/redirect?url=http://evil.com"

# Test for CORS misconfiguration
curl -H "Origin: https://evil.com" -I https://api.example.com

# Test for clickjacking
curl -sI https://example.com | grep -i X-Frame-Options

# Check TLS version
openssl s_client -connect example.com:443 -tls1_2

# Check HSTS
curl -sI https://example.com | grep -i strict-transport
```

## Authentication Headers
```bash
# Basic auth
Authorization: Basic base64(user:pass)

# Bearer token
Authorization: Bearer <JWT>

# Digest auth
Authorization: Digest username="admin", realm="...", nonce="...", uri="/", response="..."

# JWT format
header.payload.signature
# Header: {"alg":"HS256","typ":"JWT"}
```
