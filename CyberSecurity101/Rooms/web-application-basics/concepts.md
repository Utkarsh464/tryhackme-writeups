# Web Application Basics - Concepts

## HTTP Protocol
HTTP (Hypertext Transfer Protocol) is the foundation of data communication on the web. It is a stateless, application-layer protocol that follows a request-response model. A client (typically a web browser) sends an HTTP request to a server, which processes it and returns an HTTP response. Each request is independent, and the server does not retain information between requests without additional mechanisms like cookies or sessions.

## HTTP Methods
HTTP defines several request methods that indicate the desired action:
- **GET**: Retrieve a resource. GET requests should only retrieve data and have no side effects.
- **POST**: Submit data to be processed. Often used for form submissions and API calls that create resources.
- **PUT**: Replace a resource entirely with the provided data.
- **DELETE**: Remove a specified resource.
- **PATCH**: Apply partial modifications to a resource.
- **HEAD**: Identical to GET but returns only headers, no body.

## HTTP Status Codes
Status codes are three-digit numbers returned by the server to indicate the result of the request:
- **1xx (Informational)**: Request received, continuing process (e.g., 101 Switching Protocols).
- **2xx (Success)**: Request was successfully received and understood (e.g., 200 OK, 201 Created).
- **3xx (Redirection)**: Further action is needed to complete the request (e.g., 301 Moved Permanently, 302 Found).
- **4xx (Client Error)**: The request contains bad syntax or cannot be fulfilled (e.g., 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found).
- **5xx (Server Error)**: The server failed to fulfill a valid request (e.g., 500 Internal Server Error, 503 Service Unavailable).

## HTTP Headers
Headers provide additional context about the request or response:
- **Request headers**: Host, User-Agent, Accept, Accept-Language, Cookie, Authorization, Referer, Content-Type
- **Response headers**: Set-Cookie, Content-Type, Content-Length, Location, Server, Cache-Control, Strict-Transport-Security

## Cookies
Cookies are small pieces of data stored by the browser and sent with every request to the originating server. They are used for session management, personalization, and tracking. Security attributes include:
- **Secure**: Only sent over HTTPS
- **HttpOnly**: Inaccessible to JavaScript (mitigates XSS)
- **SameSite**: Controls cross-site request behavior
- **Domain/Path**: Restricts which sites can receive the cookie

## URL Structure
A URL (Uniform Resource Locator) has the format: `scheme://host:port/path?query#fragment`
- **Scheme**: Protocol (http, https)
- **Host**: Domain name or IP address
- **Port**: TCP port (default 80 for HTTP, 443 for HTTPS)
- **Path**: Resource location on the server
- **Query**: Key-value parameters starting with ?
- **Fragment**: Client-side reference starting with #

## Sessions
Since HTTP is stateless, sessions provide a way to persist state across multiple requests. A session is typically created when a user logs in, and a unique session identifier is stored in a cookie or URL parameter. The server maintains session data (user identity, preferences, cart contents) associated with this identifier.
