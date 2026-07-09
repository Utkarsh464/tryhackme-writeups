# openssl

**OpenSSL** — a robust, full-featured toolkit for TLS, SSL, and general-purpose cryptography.

## Syntax

```
openssl <command> [options] [arguments]
```

## Purpose

Generate RSA/EC keys, create and manage certificates, encrypt/decrypt files, compute hashes, connect to TLS services, and perform various cryptographic operations. Indispensable for understanding HTTPS, certificate validation, and secure communications.

## Common Commands

| Command | Description |
|---------|-------------|
| `genrsa` | Generate RSA private key |
| `req` | Create CSR or self-signed certificate |
| `x509` | Certificate display and signing |
| `s_client` | Generic TLS/SSL client for testing |
| `s_server` | Generic TLS/SSL server for testing |
| `enc` | Symmetric encryption/decryption |
| `dgst` | Compute message digests (hashes) |
| `rsa` | Manage RSA private keys |
| `pkcs12` | PKCS#12 file management |
| `cipher` | List available cipher algorithms |

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-out <file>` | Output file |
| `-in <file>` | Input file |
| `-nodes` | Do not encrypt the private key (no DES) |
| `-newkey` | Generate new key alongside CSR |
| `-keyout` | Write private key to file |
| `-days <N>` | Certificate validity in days |
| `-subj <string>` | Certificate subject (use `/CN=name`) |
| `-connect <host:port>` | Connect to remote TLS server |
| `-sha256` | Use SHA-256 digest |
| `-aes256` | Encrypt private key with AES-256 |
| `-base64` / `-A` | Base64 encoding |
| `-pbkdf2` | Use PBKDF2 key derivation |

## Examples

```bash
# Generate RSA private key (2048-bit)
openssl genrsa -out private.key 2048

# Generate a self-signed certificate
openssl req -new -x509 -key private.key -out cert.pem -days 365 -subj "/CN=example.com"

# Generate CSR for a certificate
openssl req -new -key private.key -out request.csr -subj "/CN=example.com"

# View certificate details
openssl x509 -in cert.pem -text -noout

# Connect to a TLS server and inspect its certificate
openssl s_client -connect example.com:443

# Encrypt a file with AES-256-CBC
openssl enc -aes-256-cbc -salt -in plain.txt -out encrypted.enc -pbkdf2

# Decrypt a file
openssl enc -d -aes-256-cbc -in encrypted.enc -out decrypted.txt -pbkdf2

# Compute SHA-256 hash
openssl dgst -sha256 file.txt

# Convert PFX (PKCS#12) to PEM
openssl pkcs12 -in bundle.pfx -out bundle.pem -nodes
```

## Common Mistakes

- Using weak key sizes — 1024-bit RSA is considered weak. Always use at least 2048 bits.
- Generating keys without `-nodes` — the private key will be encrypted with DES (weak) and require a password on every use.
- Self-signing certificates for production — browsers will warn users. Use Let's Encrypt or a proper CA.
- Using outdated ciphers — avoid RC4, 3DES, and MD5. Stick with AES-GCM, ChaCha20, SHA-256.
- Ignoring the `-pbkdf2` flag — older OpenSSL versions default to `-md5` for key derivation in `enc`, which is weak.
- Exposing private keys — the `.key` file must be kept secret. Use restrictive permissions (`chmod 600`).

## Real-World Usage

- **HTTPS testing:** Use `s_client` to inspect certificate chains, cipher suites, and TLS versions.
- **CTF cryptography:** Decrypt RSA-encrypted flags, crack weak keys, analyze certificate misconfigurations.
- **Certificate management:** Generate CSRs for web servers, convert between PEM/DER/PKCS12 formats.
- **File encryption:** Encrypt sensitive data at rest for secure storage.
- **Hash verification:** Verify file integrity using `openssl dgst` during forensic analysis.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed on most distributions |
| Windows | Full | Installers available from OpenSSL wiki |
| macOS | Full | Pre-installed (LibreSSL on newer versions) |

```bash
# Install on Linux
sudo apt install openssl
```
