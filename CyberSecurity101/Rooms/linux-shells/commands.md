# Commands: Linux Shells

## Shell Built-in Commands

| Command | Description | Example |
|---------|-------------|---------|
| `echo` | Print text to output | `echo "Hello World"` |
| `printf` | Format and print data | `printf "%s\n" "Hello"` |
| `read` | Read input from user | `read -p "Name: " name` |
| `alias` | Create command alias | `alias ll='ls -la'` |
| `unalias` | Remove alias | `unalias ll` |
| `source` | Execute script in current shell | `source ~/.bashrc` |
| `.` (dot) | Execute script in current shell | `. ~/.bashrc` |
| `export` | Set environment variable | `export PATH=$PATH:/new/path` |
| `set` | Set shell options or display vars | `set \| grep PATH` |
| `unset` | Unset variable or function | `unset TEMP_VAR` |
| `type` | Display command type | `type ls` |
| `command` | Run command ignoring aliases | `command ls` |

## I/O Redirection Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `>` | Redirect stdout to file (overwrite) | `ls > output.txt` |
| `>>` | Redirect stdout to file (append) | `echo "new" >> output.txt` |
| `<` | Read stdin from file | `sort < input.txt` |
| `2>` | Redirect stderr to file | `ls /nonexist 2> error.log` |
| `2>>` | Append stderr to file | `command 2>> error.log` |
| `&>` | Redirect stdout and stderr | `command &> output.log` |
| `2>&1` | Merge stderr into stdout | `command > all.log 2>&1` |
| `|` (pipe) | Pipe stdout to next command | `ls \| grep foo` |
| `|&` | Pipe both stdout and stderr | `command |& grep error` |
| `<< EOF` | Here document (inline input) | `cat << EOF > file.txt` |
| `<<<` | Here string | `grep foo <<< "foobar"` |
| `tee` | Split output to file and stdout | `ls \| tee filelist.txt` |

## Job Control

| Command/Key | Description | Example |
|-------------|-------------|---------|
| `command &` | Run in background | `sleep 30 &` |
| `Ctrl+Z` | Suspend foreground job | - |
| `bg` | Resume job in background | `bg %1` |
| `fg` | Bring job to foreground | `fg %1` |
| `jobs` | List background jobs | `jobs -l` |
| `disown` | Remove job from shell | `disown %1` |
| `nohup` | Run immune to hangups | `nohup longscript.sh &` |
| `wait` | Wait for background jobs | `wait` |
| `kill %1` | Kill background job by job ID | `kill %1` |

## Shell Scripting Constructs

| Construct | Description | Example |
|-----------|-------------|---------|
| `VAR=value` | Variable assignment | `NAME="Bob"` |
| `$VAR` | Variable expansion | `echo $NAME` |
| `${VAR}` | Parameter expansion | `${NAME:-default}` |
| `$(cmd)` | Command substitution | `DATE=$(date)` |
| `$((expr))` | Arithmetic expansion | `RESULT=$((5 + 3))` |
| `((expr))` | Arithmetic evaluation | `((i++))` |
| `[ expr ]` | Test expression (POSIX) | `[ -f "$file" ]` |
| `[[ expr ]]` | Extended test expression | `[[ $name == "Bob" ]]` |
| `((expr))` | Arithmetic test | `(( $count > 10 ))` |

## Control Flow

| Statement | Description | Example |
|-----------|-------------|---------|
| `if ... then ... fi` | Conditional execution | `if [ -f file ]; then echo exists; fi` |
| `elif` | Else if condition | `elif [ $x -gt 10 ]; then` |
| `else` | Default branch | `else echo "not found"; fi` |
| `for var in list` | Iterate over list | `for i in {1..5}; do echo $i; done` |
| `while condition` | Loop while true | `while [ $count -lt 10 ]; do ((count++)); done` |
| `until condition` | Loop until true | `until ping -c1 host; do sleep 1; done` |
| `case var in` | Pattern matching | `case $1 in start) ;; stop) ;; esac` |
| `break` | Exit loop | `break` |
| `continue` | Skip to next iteration | `continue` |

## Functions and Error Handling

| Construct | Description | Example |
|-----------|-------------|---------|
| `func_name() { }` | Define function | `greet() { echo "Hello $1"; }` |
| `function func_name` | Define function (alternative) | `function greet { echo "Hi"; }` |
| `return` | Exit function with code | `return 1` |
| `exit` | Exit script with code | `exit 0` |
| `trap` | Catch signals | `trap 'cleanup' EXIT` |
| `set -e` | Exit on error | `set -e` |
| `set -x` | Debug mode (print commands) | `set -x` |
| `set -u` | Treat unset vars as error | `set -u` |
| `set -o pipefail` | Pipe fails if any command fails | `set -o pipefail` |
