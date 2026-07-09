# Tools: Linux Shells

## Primary Shell

| Tool | Location | Purpose |
|------|----------|---------|
| Bash (Bourne Again SHell) | /bin/bash | Default Linux shell with scripting and interactive features |
| sh (Bourne Shell) | /bin/sh | POSIX-compliant shell (often linked to dash or bash) |
| Zsh (Z Shell) | /usr/bin/zsh | Extended shell with advanced features (oh-my-zsh) |
| Fish (Friendly Interactive Shell) | /usr/bin/fish | User-friendly shell with autosuggestions |

## Shell Built-in Commands

| Command | Purpose |
|---------|---------|
| `echo` | Display text to standard output |
| `printf` | Format and display data with format specifiers |
| `read` | Read input from the user or stdin |
| `alias` | Create shortcuts for commands |
| `unalias` | Remove command aliases |
| `source` or `.` | Execute commands from a file in the current shell |
| `export` | Set environment variables for child processes |
| `set` | Set shell options or display shell variables |
| `unset` | Remove variables or functions |
| `type` | Display information about command type |
| `command` | Run command ignoring shell functions |

## Shell Configuration Files

| File | Purpose |
|------|---------|
| ~/.bashrc | Per-user bash configuration for interactive non-login shells |
| ~/.bash_profile | Per-user bash configuration for login shells |
| ~/.profile | Per-user shell configuration (fallback) |
| ~/.bash_logout | Commands run when login shell exits |
| ~/.bash_history | Command history file |
| /etc/bash.bashrc | System-wide bash configuration |
| /etc/profile | System-wide login shell configuration |

## I/O Redirection Tools

| Operator | Purpose |
|----------|---------|
| `>` | Redirect stdout to file (overwrite) |
| `>>` | Redirect stdout to file (append) |
| `<` | Read stdin from file |
| `2>` | Redirect stderr to file |
| `2>>` | Append stderr to file |
| `&>` | Redirect both stdout and stderr |
| `2>&1` | Merge stderr into stdout stream |
| `|` | Pipe stdout to another command |
| `|&` | Pipe both stdout and stderr |
| `<<` | Here document (inline text input) |
| `<<<` | Here string (inline string input) |
| `tee` | Split output to file and stdout |

## Job Control Tools

| Command | Purpose |
|---------|---------|
| `&` | Run command in background |
| `bg` | Resume suspended job in background |
| `fg` | Bring background job to foreground |
| `jobs` | List active jobs with status |
| `disown` | Remove job from shell job table |
| `nohup` | Run command immune to hangups |
| `wait` | Wait for background processes to complete |
| Ctrl+Z | Suspend currently running foreground job |
| Ctrl+C | Interrupt and terminate foreground job |

## Scripting Constructs

| Construct | Purpose |
|-----------|---------|
| `if/then/elif/else/fi` | Conditional execution |
| `case/esac` | Pattern matching multi-way branch |
| `for/do/done` | Iterate over a list of items |
| `while/do/done` | Loop while condition is true |
| `until/do/done` | Loop until condition becomes true |
| `function` or `()` | Define reusable code blocks |
| `trap` | Catch signals and execute cleanup |
| `set -e` | Exit script on first error |
| `set -x` | Print commands before execution (debug) |
| `set -u` | Treat unset variables as errors |

## Text Processing Tools (Referenced)

| Tool | Purpose |
|------|---------|
| `grep` | Search text using patterns (regular expressions) |
| `sed` | Stream editor for text transformation |
| `awk` | Pattern scanning and data extraction language |
| `cut` | Extract sections from each line of input |
| `sort` | Sort lines of text |
| `uniq` | Filter repeated lines |
| `wc` | Count lines, words, and characters |
