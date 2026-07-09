# Hashing Basics — Commands

| Command | Description |
|---------|-------------|
| `md5sum file.txt` | Compute the MD5 hash of a file |
| `sha1sum file.txt` | Compute the SHA-1 hash of a file |
| `sha256sum file.txt` | Compute the SHA-256 hash of a file |
| `sha512sum file.txt` | Compute the SHA-512 hash of a file |
| `openssl dgst -md5 file.txt` | Compute MD5 hash using OpenSSL |
| `openssl dgst -sha256 file.txt` | Compute SHA-256 hash using OpenSSL |
| `echo -n "string" | md5sum` | Hash a string directly |
| `sha256sum -c checksums.txt` | Verify files against a checksum file |
| `shasum -a 256 file.txt` | Alternative SHA-256 computation (macOS) |
| `mkpasswd -m sha-512 password salt` | Generate a salted SHA-512 password hash |
| `python3 -c "import hashlib; print(hashlib.sha256(b'hello').hexdigest())"` | Compute hash using Python |
