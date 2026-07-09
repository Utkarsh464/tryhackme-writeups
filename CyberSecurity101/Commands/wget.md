# wget

**Wget** — a non-interactive command-line utility for downloading files from the web, supporting HTTP, HTTPS, and FTP protocols.

## Syntax

```
wget [options] <URL>
```

## Purpose

Download files from the web recursively or individually. Unlike curl, wget is specifically designed for downloads and excels at recursive mirroring, resuming interrupted transfers, and batch downloading from lists of URLs.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-O <file>` | Write output to a specific file |
| `-P <dir>` | Save files to a directory prefix |
| `-c` | Resume an incomplete download |
| `-b` | Background download (runs in background) |
| `-q` | Quiet mode (suppress output) |
| `-nv` | Non-verbose (errors only) |
| `--limit-rate=<rate>` | Limit download speed |
| `-r` | Recursive download |
| `-l <depth>` | Recursion depth (default 5) |
| `-np` | No parent directories in recursion |
| `-A / -R` | Accept / Reject file patterns |
| `-i <file>` | Read URLs from a file |
| `--user=<user>` | Username for FTP/HTTP auth |
| `--password=<pass>` | Password for FTP/HTTP auth |
| `--no-check-certificate` | Skip TLS verification |
| `--mirror` | Mirror a website (equivalent to `-r -N -l inf -np`) |

## Examples

```bash
# Simple download
wget https://example.com/file.zip

# Download with custom output filename
wget -O output.zip https://example.com/file.zip

# Resume an interrupted download
wget -c https://example.com/largefile.iso

# Download files listed in a text file
wget -i urls.txt

# Download with speed limit
wget --limit-rate=200k https://example.com/bigfile.zip

# Recursively download a website (limited depth)
wget -r -l 2 -np https://example.com/docs/

# Mirror an entire website
wget --mirror --convert-links --adjust-extension --page-requisites --no-parent https://example.com

# FTP download
wget --user=anonymous --password="guest" ftp://ftp.example.com/pub/file.txt

# Quiet download with background
wget -b -q https://example.com/largefile.iso
```

## Common Mistakes

- Recursive downloading without limits — `wget -r` without `-l` can download the entire internet and fill your disk.
- Not using `-np` with recursive downloads — wget follows links to parent directories and beyond the target.
- Forgetting `--no-check-certificate` on sites with self-signed certificates — commonly needed in CTF labs.
- Using wget for API testing — curl is better suited for this due to its broader protocol and header control.
- Downloading large files without `-c` — if the connection drops, you start from zero.
- Not rate-limiting on shared networks — wget will consume all available bandwidth.

## Real-World Usage

- **Website mirroring:** Download an entire website for offline analysis (common in OSINT).
- **Patch management:** Scripted download of updates and patches across many servers.
- **CTF file retrieval:** Download exploit scripts, tools, or payloads onto a target machine.
- **Data exfiltration (simulated):** In labs, test how large file transfers appear on the network.
- **Automated backups:** Pull remote backups from FTP/HTTP servers via cron.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed on most distributions |
| Windows | Limited | Available via WSL or `choco install wget` |
| macOS | Full | Pre-installed on older versions, install via brew |

```bash
# Install on Linux
sudo apt install wget
```
