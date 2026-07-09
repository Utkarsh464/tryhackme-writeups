# Concepts: HTTP in Detail

## 1. HTTP Protocol
HTTP is a stateless, text-based request-response protocol. A client (usually a browser) sends a request to a server, which returns a response. The request includes a method, path, HTTP version, headers, and optionally a body. The response includes a status code, headers, and optionally a body.

## 2. GET Method
GET requests retrieve data from a server. Parameters are sent in the URL query string. GET requests are idempotent (multiple identical requests produce the same result) and should not cause side effects. GET requests can be cached and bookmarked.

## 3. POST Method
POST requests send data to a server, typically to create a new resource. Data is in the request body, not the URL. POST requests are not idempotent — submitting a form twice can create duplicate entries. POST data can be form-encoded, JSON, or multipart.

## 4. 2xx Success Codes
200 OK is the standard success response. 201 Created indicates a resource was created (POST). 204 No Content means success but no response body (DELETE). 206 Partial Content is used for range requests (video streaming, downloads).

## 5. 4xx Client Error Codes
400 Bad Request indicates malformed syntax. 401 Unauthorized requires authentication. 403 Forbidden means the server understood but refuses. 404 Not Found is the most recognized — resource doesn't exist. 405 Method Not Allowed means the method isn't supported for that URL.

## 6. HTTP Headers
Headers carry metadata about the request or response. The Host header is required in HTTP/1.1 and enables virtual hosting. Cookies (Set-Cookie/Cookie) maintain session state. CORS headers control cross-origin requests. Content-Type defines the body format (text/html, application/json).

## 7. HTTPS and TLS
HTTPS = HTTP over TLS. TLS (Transport Layer Security) provides encryption, server authentication (via certificates), and message integrity. The TLS handshake involves cipher suite negotiation, certificate exchange, and key generation. Without HTTPS, all data including passwords and cookies is sent in plaintext.

## 8. Statelessness and Sessions
HTTP is stateless — each request is independent. To maintain state (e.g., user logged in), servers use cookies: the server sends a Set-Cookie header, and the client includes it in subsequent requests via the Cookie header. Session IDs stored in cookies map to server-side session data.
