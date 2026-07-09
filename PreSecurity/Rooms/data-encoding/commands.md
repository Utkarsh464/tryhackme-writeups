# Commands: Data Encoding

## Linux Commands

| Command | Description |
|---------|-------------|
| `echo -n "text" \| base64` | Encode text to base64 |
| `echo "dGV4dA==" \| base64 -d` | Decode base64 to text |
| `echo -n "hello" \| xxd -p` | Encode to hex |
| `echo "68656c6c6f" \| xxd -r -p` | Decode hex to text |
| `printf '%s' "hello" \| od -A x -t x1z` | Display hex dump |
| `man ascii` | View ASCII table documentation |

## Python Commands

| Command | Description |
|---------|-------------|
| `"hello".encode("utf-8")` | Encode string to UTF-8 bytes |
| `b"hello".decode("utf-8")` | Decode UTF-8 bytes to string |
| `import base64; base64.b64encode(b"text")` | Encode bytes to base64 |
| `import base64; base64.b64decode(b"dGV4dA==")` | Decode base64 to bytes |
| `import urllib.parse; urllib.parse.quote("a b")` | URL encode a string |
| `import urllib.parse; urllib.parse.unquote("a%20b")` | URL decode a string |
| `"hello".encode().hex()` | Encode string to hex |
| `bytes.fromhex("68656c6c6f")` | Decode hex to bytes |
