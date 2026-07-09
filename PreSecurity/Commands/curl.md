# curl

## Syntax
`curl [options] URL`

## Purpose
Transfers data to/from servers using various protocols (HTTP, HTTPS, FTP, etc.). Essential for web reconnaissance and API testing.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-L` | Follow redirects |
| `-o FILE` | Write output to file |
| `-O` | Save with remote filename |
| `-H "Header: value"` | Add custom header |
| `-d "data"` | Send POST data |
| `-X METHOD` | Specify HTTP method |
| `-k` | Allow insecure SSL connections |
| `-v` | Verbose (show request/response details) |

## Examples
```bash
curl https://example.com
curl -L -O https://example.com/file.zip
curl -X POST -d "user=admin&pass=test" https://example.com/login
curl -H "Authorization: Bearer TOKEN" https://api.example.com/users
curl -v -k https://selfsigned.local
```

## Compatibility
Linux | Windows | macOS