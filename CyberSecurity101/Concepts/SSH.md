# SSH

## Definition
SSH (Secure Shell) is a cryptographic network protocol for operating network services securely over an unsecured network. It provides encrypted remote login, command execution, and file transfer capabilities. Replacing insecure protocols like Telnet, rlogin, and FTP, SSH is the standard for remote administration of servers, network devices, and cloud instances.

## Why It Matters
SSH is the universal tool for managing remote systems in enterprise IT. In cybersecurity, SSH is used for secure access to penetration testing targets, tunneling traffic through firewalls, forwarding ports for pivoting, and securely transferring tools and data. Understanding SSH authentication, key management, and tunneling is essential for both red and blue teams.

## Where It Appears in the Path
SSH is introduced in the Linux module for remote server access. It is a prerequisite for penetration testing (accessing targets), network pivoting, and secure file transfers. SSH key management appears in cryptography and authentication topics.

## Prerequisites
- Basic Linux command line
- Networking (ports, TCP)

## Authentication Methods

### Password Authentication
The user enters a password sent over the encrypted channel. Simple but vulnerable to brute-force attacks. Should be disabled in production in favor of key-based auth.

### Public Key Authentication
Uses asymmetric cryptography (RSA, ECDSA, Ed25519). The user generates a key pair (`ssh-keygen`), places the public key on the server (`~/.ssh/authorized_keys`), and keeps the private key locally. During authentication:
1. Server sends a challenge encrypted with the public key.
2. Client decrypts with the private key and responds.
3. Server verifies the response. No password is transmitted.

### Host-Based Authentication
Trusts the client host (not just the user). Rarely used in practice due to security concerns.

### Keyboard-Interactive
Multi-factor authentication (password + OTP), challenge-response.

## Key File Formats
- **PEM**: Traditional format (`-----BEGIN RSA PRIVATE KEY-----`), sometimes called OpenSSH legacy format.
- **OpenSSH**: Newer format (`-----BEGIN OPENSSH PRIVATE KEY-----`), uses bcrypt for key derivation.
- **PuTTY (.ppk)**: Windows PuTTY format. Convert with `puttygen` or `ssh-keygen`.

## SSH Tunneling
SSH can create encrypted tunnels for other protocols.

### Local Port Forwarding
Forward a local port to a remote destination through the SSH server.
```
ssh -L 8080:internal-server:80 user@gateway
```
Accessing `localhost:8080` tunnels to `internal-server:80` through the gateway.

### Remote Port Forwarding
Forward a remote port back to a local service.
```
ssh -R 8080:localhost:3000 user@public-server
```
Traffic to `public-server:8080` is tunneled to `localhost:3000`.

### Dynamic Port Forwarding (SOCKS Proxy)
Creates a SOCKS5 proxy on the client.
```
ssh -D 1080 user@server
```
Configure applications to use SOCKS proxy at `localhost:1080` — all traffic tunnels through the SSH server.

## SSH Agent and Agent Forwarding
- **ssh-agent**: Stores decrypted private keys in memory so users don't re-enter passphrases.
- **Agent Forwarding (`-A`)**: Allows the remote server to use the local agent for authentication. Useful for "jump box" scenarios. Security risk: root on the remote server can use the agent while connected.

## SSH Config File
`~/.ssh/config` simplifies connections:
```
Host myserver
    HostName 192.168.1.100
    User admin
    Port 2222
    IdentityFile ~/.ssh/mykey
```

## Common Attacks
- **Brute Force**: Automated password guessing. Mitigated by disabling password auth, using key-only auth, fail2ban, rate limiting.
- **Man-in-the-Middle**: Compromised SSH client or DNS to intercept connections. Mitigated by verifying host keys (`ssh -k`, host key fingerprint).
- **SSH Key Theft**: Stolen private keys. Mitigated by passphrase protection, key expiration, hardware security keys (YubiKey for SSH).
- **SSH Compromise (CVE-2024-6387)**: Recent vulnerabilities in OpenSSH software.

## Common Interview Questions
1. **How does SSH public key authentication work?** The server uses the stored public key to create a challenge. The client's private key must decrypt it. This proves possession of the private key without transmitting it.
2. **What is the difference between SSH local and remote port forwarding?** Local forward = remote machine accesses its network through your connection. Remote forward = your machine accesses a remote network through the server's connection.
3. **How do you secure an SSH server?** Disable root login (`PermitRootLogin no`), disable password auth (`PasswordAuthentication no`), use key-only auth, change default port (security by obscurity, not real security), use fail2ban, enforce Protocol 2, use Ed25519 keys, configure AllowUsers.
4. **What is SSH agent forwarding and why is it dangerous?** Passes your SSH agent socket to the remote server, allowing it to authenticate to other servers as you. Dangerous because an admin/attacker with root on the remote server can hijack your agent.
5. **Explain the SSH handshake.** Key exchange (Diffie-Hellman) → Server authentication (host key) → Session key derivation → Client authentication (password or public key) → Encrypted channel.
6. **What ports does SSH use?** Default port 22/tcp. Can be configured to any port. SCP/SFTP run over SSH (same port).

## Further Reading
- [OpenSSH Manual](https://www.openssh.com/manual.html)
- [SSH Academy](https://www.ssh.com/academy)
- `man ssh`, `man sshd`, `man ssh-keygen`, `man ssh_config`
- DigitalOcean SSH Essentials
- _SSH Mastery_ by Michael Lucas
