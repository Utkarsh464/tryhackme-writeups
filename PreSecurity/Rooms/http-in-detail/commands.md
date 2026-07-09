# Commands: HTTP in Detail

## curl Requests

| Command | Description |
|---------|-------------|
| `curl http://example.com` | Basic GET request |
| `curl -I http://example.com` | Fetch only response headers |
| `curl -v http://example.com` | Verbose output with request/response headers |
| `curl -X POST -d "username=admin&password=pass" http://example.com/login` | POST request with form data |
| `curl -X PUT -d '{"key":"value"}' -H "Content-Type: application/json" http://example.com/api` | PUT request with JSON body |
| `curl -X DELETE http://example.com/resource/1` | DELETE request |
| `curl -H "Authorization: Bearer token123" http://example.com/api` | Request with authorization header |
| `curl -b "session=abc123" http://example.com/dashboard` | Send cookies with request |
| `curl -k https://example.com` | Skip TLS certificate verification |
| `curl --path-as-is http://example.com/../etc/passwd` | Prevent curl from normalizing paths |

## Netcat

| Command | Description |
|---------|-------------|
| `echo -e "GET / HTTP/1.1\r\nHost: example.com\r\n\r\n" \| nc example.com 80` | Manual HTTP request with netcat |
