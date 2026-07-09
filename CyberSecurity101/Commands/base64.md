# base64

**Base64 Encoding/Decoding** — a command-line utility for encoding binary data into ASCII text using the Base64 scheme, and decoding it back.

## Syntax

```
base64 [options] [file]
```

## Purpose

Encode binary data into a portable ASCII format for transmission over text-based protocols (email, HTTP headers, JSON). Commonly used in CTF challenges for hiding flags, obfuscating data, and encoding credentials.

## How Base64 Works

Base64 maps every 3 bytes of binary data (24 bits) into 4 ASCII characters (6 bits each). The alphabet includes `A-Z`, `a-z`, `0-9`, `+`, and `/`. Padding (`=`) is added to make the output length a multiple of 4.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-d` / `--decode` | Decode base64-encoded data |
| `-i` / `--ignore-garbage` | Ignore non-alphabet characters during decode |
| `-w <cols>` | Wrap output at specified column (default 76, `0` = no wrap) |
| `-n` | Do not add trailing newline (GNU coreutils) |

## Examples

```bash
# Encode a string
echo "Hello World" | base64
# Output: SGVsbG8gV29ybGQK

# Decode a string
echo "SGVsbG8gV29ybGQK" | base64 -d
# Output: Hello World

# Encode a file
base64 file.txt > file.txt.b64

# Decode a file
base64 -d file.txt.b64 > file.txt

# Encode without line wrapping (single line)
echo "data" | base64 -w 0

# Decode with garbage ignored
echo "SGV$%sGxvIF$%dvcmxk" | base64 -d -i 2>/dev/null

# Encode binary data (e.g., an image)
base64 -w 0 image.png > image.b64

# Decode base64 back to binary
base64 -d image.b64 > image.png

# Encode with Python (alternative)
python3 -c "import base64; print(base64.b64encode(b'Hello'))"

# Multiple decodes (sometimes data is double-encoded)
echo "U0dWc2JHOD0K" | base64 -d | base64 -d
```

## Common Mistakes

- Not using `-d` to decode — base64 encodes by default. Forgetting `-d` re-encodes already-encoded data.
- Assuming base64 is encryption — it is encoding, not encryption. Data is trivially reversible.
- Ignoring padding (`=`) — missing or incorrect padding causes decode errors.
- Forgetting `-w 0` when encoding binary data — default line wrapping (76 chars) breaks the base64 string into multiple lines, which may break single-line expectations.
- Using `echo` which adds a trailing newline — `echo "text" | base64` includes the newline in the encoded output. Use `printf` or `echo -n` to avoid this.
- Confusing base64 with base64url — URL-safe base64 uses `-` and `_` instead of `+` and `/`.

## Real-World Usage

- **CTF challenges:** Decode base64 strings to reveal flags (`echo "VEhNe30=" | base64 -d`).
- **Authorization headers:** Encode `username:password` for HTTP Basic Auth.
- **Binary data transfer:** Embed images in HTML/CSS as data URIs (`data:image/png;base64,...`).
- **Email attachments:** MIME encoding uses base64 for binary attachments.
- **Credential storage:** Obfuscate API keys or tokens (not secure, but common).

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (GNU coreutils) |
| Windows | Limited | `certutil -encode` / `certutil -decode`, or PowerShell |
| macOS | Full | Pre-installed (BSD base64) |

```bash
# base64 is pre-installed on Linux/macOS
```
