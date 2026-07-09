# Bash

## Definition
Bash (Bourne Again SHell) is a Unix shell and command language. It is the default shell on most Linux distributions and macOS, acting as both an interactive command interpreter and a scripting language. Bash provides features like command-line editing, job control, aliases, functions, and shell scripting with variables, control flow, and I/O redirection.

## Why It Matters
Bash is the primary interface for Linux system administration, DevOps, and cybersecurity operations. In penetration testing, Bash is used to automate reconnaissance, parse tool output, chain exploits, and create post-exploitation scripts. In defensive security, Bash scripts automate log analysis, system hardening, monitoring, and incident response. Without Bash proficiency, a cybersecurity professional is severely limited in Linux environments.

## Where It Appears in the Path
Bash is introduced in the Linux fundamentals module. It is prerequisite for scripting, automation, penetration testing (running tools, chaining commands), log analysis, and any advanced Linux usage throughout the path.

## Prerequisites
- Basic Linux command-line familiarity (ls, cd, cp, rm)
- File system hierarchy understanding

## Variables
```bash
name="Alice"
echo "Hello, $name!"   # Variable expansion
echo "Length: ${#name}"  # String length
readonly pi=3.14       # Read-only variable
unset name             # Remove variable
```

### Special Variables
- `$0`: Script name
- `$1`, `$2`, ...: Positional parameters
- `$#`: Number of arguments
- `$@`: All arguments as array
- `$*`: All arguments as single string
- `$?`: Exit status of last command
- `$$`: Current process PID
- `$!`: PID of last background process

## Control Flow

### Conditionals
```bash
if [ "$name" = "Alice" ]; then
    echo "Hello Alice"
elif [ -f "/etc/passwd" ]; then
    echo "File exists"
else
    echo "Default"
fi
```

### Test operators
- `[ -f file ]` — file exists and is regular
- `[ -d dir ]` — directory exists
- `[ -x file ]` — file is executable
- `[ -z string ]` — string is empty
- `[ string1 = string2 ]` — string equality
- `[ num1 -gt num2 ]` — numeric greater than

### Loops
```bash
for i in {1..5}; do echo $i; done
for file in /etc/*.conf; do echo $file; done
while [ "$count" -lt 10 ]; do echo $count; ((count++)); done
until [ "$count" -ge 10 ]; do echo $count; ((count++)); done
```

### Functions
```bash
function greet() {
    local name=$1
    echo "Hello, $name"
}
greet "World"
```

## I/O Redirection and Pipes
- `>` — Redirect stdout (overwrite)
- `>>` — Redirect stdout (append)
- `2>` — Redirect stderr
- `&>` — Redirect both stdout and stderr
- `<` — Redirect stdin from file
- `|` — Pipe stdout of one command to stdin of another
- `<<EOF` — Here document (inline input)
- `tee` — Split output to file and stdout

## Command Substitution
```bash
current_date=$(date +%Y-%m-%d)
files_count=$(ls /etc | wc -l)
```

## Common Scripting Patterns

### Error Handling
```bash
set -euo pipefail  # Exit on error, undefined vars, pipe failures
trap 'echo "Error on line $LINENO"' ERR  # Error handler
```

### Parsing Arguments
```bash
while getopts "u:p:h" opt; do
    case $opt in
        u) user="$OPTARG" ;;
        p) pass="$OPTARG" ;;
        h) usage; exit 0 ;;
        *) usage; exit 1 ;;
    esac
done
```

## Security Scripting Examples

### Network Scan
```bash
#!/bin/bash
for ip in $(seq 1 254); do
    ping -c 1 -W 1 192.168.1.$ip | grep "64 bytes" | cut -d" " -f4 | tr -d ":" &
done
```

### Log Monitoring
```bash
tail -f /var/log/auth.log | while read line; do
    if echo "$line" | grep -q "Failed password"; then
        echo "ALERT: Failed SSH login attempt"
    fi
done
```

## Common Interview Questions
1. **What is the difference between `$@` and `$*`?** `$@` preserves argument boundaries (array), `$*` joins all arguments into one string.
2. **Explain I/O redirection in Bash.** `>` overwrites, `>>` appends, `2>` for stderr, `&>` for both, `<` for input, `|` for piping.
3. **What is the difference between single and double quotes in Bash?** Single quotes preserve literal meaning (no expansion). Double quotes allow variable expansion and command substitution.
4. **How do you debug a Bash script?** `bash -x script.sh`, `set -x` inside script, `trap` for error handling, `echo` statements.
5. **What is the purpose of `set -e`?** Exit immediately if any command exits with a non-zero status (prevents continuing after errors).
6. **How do you check if a file exists in Bash?** `[ -f "/path/to/file" ]` returns true if file exists and is a regular file.

## Further Reading
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html)
- _Bash Guide for Beginners_ by Machtelt Garrels
- _The Linux Command Line_ by William Shotts
- [ShellCheck](https://www.shellcheck.net/) (Bash linting)
- **Google Shell Style Guide**
- OverTheWire Bandit (practice)
