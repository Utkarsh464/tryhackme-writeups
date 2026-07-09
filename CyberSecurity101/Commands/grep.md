# grep

**Global Regular Expression Print** — a command-line utility for searching plain-text data for lines matching a regular expression.

## Syntax

```
grep [options] <pattern> [file...]
```

## Purpose

Search through files or input streams for lines that match a specified pattern. Indispensable for log analysis, source code searching, output filtering, and data extraction in penetration testing and system administration.

## Common Parameters

| Parameter | Description |
|-----------|-------------|
| `-i` | Case-insensitive search |
| `-v` | Invert match (show lines NOT matching) |
| `-r` / `-R` | Recursive directory search |
| `-l` | List only filenames with matches |
| `-n` | Show line numbers |
| `-c` | Count matching lines |
| `-w` | Match whole words only |
| `-x` | Match whole lines only |
| `-E` | Extended regex (ERE, same as `egrep`) |
| `-P` | Perl-compatible regex (PCRE) |
| `-o` | Show only matched part |
| `-A <N>` | Show N lines after match |
| `-B <N>` | Show N lines before match |
| `-C <N>` | Show N lines before and after match (context) |
| `--color` | Highlight matches (usually auto-enabled) |
| `-H` | Always print filename header |

## Examples

```bash
# Search for a string in a file
grep "password" server.log

# Case-insensitive search
grep -i "error" /var/log/syslog

# Recursive search for IP addresses in a directory
grep -rn "10\.10\.10\." /var/log/

# Show context (3 lines before and after)
grep -C 3 "failed password" auth.log

# List files containing a pattern
grep -rl "admin" /var/www/

# Count occurrences
grep -c "GET /" access.log

# Invert match (exclude debug lines)
grep -v "DEBUG" app.log

# Extended regex — find emails
grep -E "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}" file.txt

# Whole word match
grep -w "secret" file.txt

# Pipe from other commands
ps aux | grep "apache"
history | grep "nmap"

# Find lines with only numbers
grep -x -E "[0-9]+" file.txt
```

## Common Mistakes

- Forgetting `-i` when case might vary — `Error` is different from `error` and `ERROR`.
- Not quoting the pattern — special characters like `.` `*` `[` `(` will be interpreted by the shell.
- Using basic regex when extended is needed — `+`, `?`, `{`, `}`, `(`, `)` need escaping in BRE or use `-E`.
- Binary file warnings — use `-a` to treat binary as text, or `-I` to skip binaries entirely.
- Missing `-r` for directory searches — grep on a directory without `-r` shows an error.

## Real-World Usage

- **Log analysis:** Find error messages, authentication failures, suspicious HTTP requests in web logs.
- **CTF challenges:** Search through files for flag patterns (`grep -r "THM{" *`).
- **Output filtering:** Chain commands with pipes to extract relevant data (e.g., `ss -tuln | grep 22`).
- **Code auditing:** Find hardcoded credentials, API keys, or insecure functions.
- **Forensics:** Search disk images or large file dumps for specific keywords.

## Compatibility

| OS | Support | Notes |
|----|---------|-------|
| Linux | Full | Pre-installed (GNU grep) |
| Windows | Limited | `findstr` is the closest equivalent, or use WSL |
| macOS | Full | Pre-installed (BSD grep, slightly different flags) |

```bash
# Install on Linux (usually pre-installed)
sudo apt install grep
```
