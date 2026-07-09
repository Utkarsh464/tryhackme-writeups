# ssh

**Secure Shell** — a cryptographic network protocol for operating network services securely over an unsecured network.

## Syntax

```
ssh [options] <user>@<host> [command]
```

## Purpose

Securely log into remote systems, execute commands on remote machines, forward ports, and transfer files. The standard protocol for remote administration of Linux/Unix systems.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-p <port>` | Specify port (default 22) |
| `-i <file>` | Identity file (private key) for authentication |
| `-l <user>` | Login name (alternative to `user@host`) |
| `-v` | Verbose mode (debug connection issues) |
| `-vvv` | Maximum verbosity |
| `-N` | Do not execute a remote command (for port forwarding) |
| `-L <local:host:remote>` | Local port forwarding |
| `-R <remote:host:local>` | Remote port forwarding |
| `-D <port>` | Dynamic forwarding (SOCKS proxy) |
| `-o <option>` | Specify options (e.g., `-o StrictHostKeyChecking=no`) |
| `-J <user@jump>` | Jump host / bastion connection |
| `-A` | Forward SSH agent |

## Examples

```bash
# Basic SSH login
ssh user@10.10.10.1

# SSH on non-standard port
ssh -p 2222 user@10.10.10.1

# Use specific private key
ssh -i ~/.ssh/id_rsa user@10.10.10.1

# Execute a single command on remote host
ssh user@10.10.10.1 "ls -la /var/log"

# Local port forwarding (localhost:8080 -> remote:80)
ssh -L 8080:localhost:80 user@10.10.10.1

# Remote port forwarding (remote:8080 -> localhost:80)
ssh -R 8080:localhost:80 user@10.10.10.1

# Dynamic SOCKS proxy on port 9050
ssh -D 9050 user@10.10.10.1

# Disable host key checking (use with caution)
ssh -o StrictHostKeyChecking=no user@10.10.10.1

# Connect via jump host
ssh -J jumpuser@jumpbox:22 user@target:2222
```

## SSH Key Generation

```bash
# Generate RSA key pair
ssh-keygen -t rsa -b 4096 -f ~/.ssh/thm_key

# Copy public key to remote server
ssh-copy-id -i ~/.ssh/thm_key.pub user@10.10.10.1

# Or manually
cat ~/.ssh/id_rsa.pub | ssh user@10.10.10.1 "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

## Common Mistakes

- Using password authentication over SSH when key-based auth is available — passwords are brute-forceable.
- Setting `StrictHostKeyChecking=no` globally — exposes you to MITM attacks. Use only per-host or in isolated labs.
- Exposing SSH to the internet on the default port without fail2ban — attracts constant brute-force attempts.
- Forgetting to set proper permissions on `~/.ssh` (700) and `authorized_keys` (600) — SSH silently ignores keys with wrong permissions.
- Using `-v` only once — use `-vvv` for maximum debugging information.
- Leaving SSH agent forwarding enabled unnecessarily — permits anyone with root on the remote host to use your keys.

## Real-World Usage

- **Remote administration:** Manage Linux servers, deploy configs, install updates.
- **Penetration testing:** SSH into compromised hosts, set up tunnels to access internal networks.
- **CTF challenges:** Connect to target machines, forward ports to access internal services.
- **Port forwarding:** Access internal services through a compromised host without exposing them.
- **Secure file transfer:** Use SCP or SFTP (both use SSH) to transfer files securely.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (OpenSSH) |
| Windows | Full | Native OpenSSH client since Windows 10 |
| macOS | Full | Pre-installed (OpenSSH) |

```bash
# Install SSH client and server on Linux
sudo apt install openssh-client openssh-server
```
