# Web Application Basics - Commands

## curl

| Command | Description |
|---------|-------------|
| `curl http://example.com` | Send a basic GET request |
| `curl -v http://example.com` | Send a GET request with verbose output (shows headers) |
| `curl -X POST http://example.com/login -d "user=admin&pass=123"` | Send a POST request with form data |
| `curl -X PUT http://example.com/api/resource/1 -d '{"name":"test"}'` | Send a PUT request with JSON data |
| `curl -X DELETE http://example.com/api/resource/1` | Send a DELETE request |
| `curl -H "Authorization: Bearer token123" http://example.com/api` | Send a request with a custom header |
| `curl -H "Cookie: session=abc123" http://example.com/dashboard` | Send a request with a cookie |
| `curl -o output.html http://example.com` | Save response body to a file |
| `curl -L http://example.com` | Follow redirects automatically |
| `curl -k https://example.com` | Skip SSL certificate validation (insecure) |

## Developer Tools (Browser)

| Key Binding | Description |
|-------------|-------------|
| `F12` or `Ctrl+Shift+I` | Open developer tools |
| `Ctrl+Shift+E` | Open Network tab (Firefox) |
| `Ctrl+R` | Reload page and capture network traffic |
| Click request row | Inspect request/response details |

## netcat

| Command | Description |
|---------|-------------|
| `nc -lvnp 8080` | Listen on a port to receive HTTP requests |
| `echo -e "GET / HTTP/1.1\r\nHost: example.com\r\n\r\n" \| nc example.com 80` | Craft a raw HTTP request |
