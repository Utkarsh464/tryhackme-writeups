# Web Security Cheat Sheet

## HTTP Methods
| Method | Purpose | Idempotent |
|--------|---------|------------|
| GET | Retrieve resource | Yes |
| POST | Create/submit | No |
| PUT | Replace/update | Yes |
| PATCH | Partial update | No |
| DELETE | Remove resource | Yes |
| HEAD | Headers only (like GET) | Yes |
| OPTIONS | Available methods | Yes |

## Status Codes
| Code | Meaning |
|------|---------|
| 200 | OK |
| 201 | Created |
| 204 | No Content |
| 301 | Moved Permanently |
| 302 | Found (temporary redirect) |
| 304 | Not Modified (cache) |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 405 | Method Not Allowed |
| 429 | Too Many Requests |
| 500 | Internal Server Error |
| 502 | Bad Gateway |
| 503 | Service Unavailable |

## Common Headers
| Header | Example | Purpose |
|--------|---------|---------|
| `Host` | `Host: example.com` | Target hostname |
| `User-Agent` | `User-Agent: curl/7.8` | Client identity |
| `Content-Type` | `Content-Type: application/json` | Body format |
| `Authorization` | `Authorization: Bearer tok` | Authentication |
| `Cookie` | `Cookie: session=abc` | Session data |
| `Set-Cookie` | `Set-Cookie: session=abc; HttpOnly` | Server sets cookie |
| `Location` | `Location: /login` | Redirect target |
| `Content-Security-Policy` | `default-src 'self'` | XSS prevention |
| `X-Frame-Options` | `DENY` | Clickjacking prevention |
| `Strict-Transport-Security` | `max-age=31536000` | HSTS |