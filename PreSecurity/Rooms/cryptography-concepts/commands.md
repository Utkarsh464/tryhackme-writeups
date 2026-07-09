# Commands: Cryptography Concepts

## OpenSSL Encryption

| Command | Description |
|---------|-------------|
| `openssl enc -aes-256-cbc -in f -out f.enc` | Encrypt file with AES-256-CBC |
| `openssl enc -d -aes-256-cbc -in f.enc -out f` | Decrypt AES-256-CBC file |
| `openssl genrsa -out private.pem 2048` | Generate RSA private key |
| `openssl rsa -pubout -in private.pem -out public.pem` | Extract RSA public key |
| `openssl rsautl -encrypt -pubin -inkey pub.pem -in f -out f.enc` | Encrypt with RSA public key |
| `openssl rsautl -decrypt -inkey private.pem -in f.enc -out f` | Decrypt with RSA private key |

## Hashing

| Command | Description |
|---------|-------------|
| `sha256sum file.txt` | SHA-256 hash of a file |
| `md5sum file.txt` | MD5 hash of a file |
| `echo -n "data" \| sha256sum` | Hash a string |
| `openssl dgst -sha256 file.txt` | OpenSSL SHA-256 hash |

## Digital Signatures

| Command | Description |
|---------|-------------|
| `openssl dgst -sha256 -sign private.pem -out sig file` | Sign a file |
| `openssl dgst -sha256 -verify public.pem -signature sig file` | Verify a signature |

## Certificate Inspection

| Command | Description |
|---------|-------------|
| `openssl s_client -connect example.com:443` | View TLS certificate |
| `openssl x509 -in cert.pem -text -noout` | Decode and display certificate |
| `openssl x509 -in cert.pem -dates -noout` | Show certificate validity dates |
