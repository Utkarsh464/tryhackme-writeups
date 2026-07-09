# Public Key Cryptography Basics — Commands

Commands for working with public key cryptography:

| Command | Description |
|---------|-------------|
| `openssl genrsa -out private.pem 4096` | Generate a 4096-bit RSA private key |
| `openssl rsa -in private.pem -pubout -out public.pem` | Extract the RSA public key |
| `openssl req -new -key private.pem -out cert.csr` | Generate a Certificate Signing Request |
| `openssl x509 -req -in cert.csr -signkey private.pem -out cert.pem` | Self-sign a certificate |
| `openssl x509 -in cert.pem -text -noout` | View certificate details in human-readable form |
| `openssl s_client -connect example.com:443` | Connect to a TLS server and display its certificate chain |
| `openssl dhparam -out dhparams.pem 2048` | Generate Diffie-Hellman parameters |
