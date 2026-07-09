# Networking Secure Protocols — Commands

Commands referenced for interacting with secure protocols:

| Command | Description |
|---------|-------------|
| `ssh user@host` | Establish an encrypted SSH connection to a remote host |
| `sftp user@host` | Start an SFTP session for secure file transfer |
| `openssl s_client -connect host:443` | Connect to a TLS server and display certificate details |
| `curl -v https://example.com` | Make an HTTPS request with verbose TLS handshake output |
| `ssh-keygen` | Generate SSH key pairs for authentication |
| `dig example.com +dnssec` | Query DNSSEC records for a domain |
| `iptables` | Configure IPsec policies on Linux |
