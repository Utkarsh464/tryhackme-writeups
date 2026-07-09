# Cryptography Basics — Commands

Commands referenced for cryptographic operations:

| Command | Description |
|---------|-------------|
| `openssl enc -aes-256-cbc -salt -in plain.txt -out cipher.enc` | Encrypt a file with AES-256-CBC |
| `openssl enc -d -aes-256-cbc -in cipher.enc -out plain.txt` | Decrypt an AES-256-CBC file |
| `openssl genrsa -out private.pem 2048` | Generate an RSA private key |
| `openssl rsa -in private.pem -pubout -out public.pem` | Extract the public key from an RSA key pair |
| `openssl rsautl -encrypt -in plain.txt -out cipher.enc -pubin -inkey public.pem` | Encrypt with RSA public key |
| `openssl rsautl -decrypt -in cipher.enc -out plain.txt -inkey private.pem` | Decrypt with RSA private key |
| `echo "plaintext" | base64` | Base64 encode (encoding, not encryption) |
| `echo "ciphertext" | base64 -d` | Base64 decode |
