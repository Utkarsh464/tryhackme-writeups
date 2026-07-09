# Bash Scripting Cheat Sheet

## Shebang & Basics
```bash
#!/bin/bash
set -euo pipefail  # Exit on error, unset vars, pipefail
set -x            # Debug mode (print commands)
```

## Variables
```bash
name="value"                    # Assignment (no spaces)
readonly CONST="fixed"          # Read-only variable
local var="scope"               # Local in function
export ENV_VAR="exported"       # Environment variable
${var:-default}                 # Default value if unset
${var:=default}                 # Assign default if unset
${var:?error}                   # Exit if unset
${var:+alt}                     # Alternate if set
${#var}                         # Length
${var:offset:len}               # Substring
${var/pattern/replacement}      # Replace first
${var//pattern/replacement}     # Replace all
${var%pattern}                  # Remove suffix
${var#pattern}                  # Remove prefix
```

## Arrays
```bash
arr=("a" "b" "c")
${arr[0]}                       # Index access
${arr[@]}                       # All elements
${#arr[@]}                      # Length
arr+=("d")                      # Append
```

## Conditionals
```bash
if [[ condition ]]; then ...; fi
[[ -z "$var" ]]      # String is empty
[[ -n "$var" ]]      # String not empty
[[ "$a" == "$b" ]]   # String equal
[[ "$a" != "$b" ]]   # String not equal
[[ "$a" =~ regex ]]  # Regex match
[[ $a -eq $b ]]      # Numeric equal (-ne, -lt, -le, -gt, -ge)
[[ -f file ]]        # File exists
[[ -d dir ]]         # Directory exists
[[ -r file ]]        # Readable
[[ -w file ]]        # Writable
[[ -x file ]]        # Executable
[[ -e file ]]        # Exists (any type)
[[ -s file ]]        # Not empty
[[ ! condition ]]    # Negate
[[ cond1 && cond2 ]] # AND
[[ cond1 || cond2 ]] # OR
```

## Loops
```bash
for i in {1..10}; do echo $i; done
for ((i=0; i<10; i++)); do echo $i; done
for file in *.txt; do echo $file; done
while read line; do echo $line; done < file
until condition; do ...; done
break           # Exit loop
continue        # Next iteration
```

## Functions
```bash
function_name() {
    local arg1=$1
    local arg2=$2
    echo "Args: $@, Count: $#"
    return 0
}
function_name "hello" "world"
```

## Redirections
| Operator | Effect |
|----------|--------|
| `>` | stdout to file (overwrite) |
| `>>` | stdout to file (append) |
| `2>` | stderr to file |
| `2>&1` | stderr to stdout |
| `&>` | both to file |
| `<` | input from file |
| `<<< "str"` | here-string |
| `<< EOF ... EOF` | here-document |
| `cmd1 \| cmd2` | pipe stdout to cmd2 |
| `cmd1 2>&1 \| cmd2` | pipe both streams |
| `cmd &` | background |
| `cmd1 && cmd2` | run if prev succeeds |
| `cmd1 \|\| cmd2` | run if prev fails |

## Special Characters
| Char | Purpose |
|------|---------|
| `$()` | Command substitution |
| `$(())` | Arithmetic expansion |
| `(( ... ))` | Arithmetic context |
| `''` | Literal string |
| `""` | String with variable expansion |
| `` ` `` | Legacy command substitution |
| `\ ` | Escape character |
| `#` | Comment |
| `;` | Command separator |
| `*` | Wildcard (any chars) |
| `?` | Wildcard (single char) |
| `[abc]` | Character class |
| `~` | Home directory |

## Useful Constructs
```bash
# Read file line by line
while IFS= read -r line; do ...; done < file

# Check command exit status
if cmd; then echo "success"; fi

# Get exit code of last command
echo $?

# Select menu
select opt in "a" "b"; do case $opt in ...);; esac; done

# Case statement
case "$var" in
    pattern1) cmd1 ;;
    pattern2) cmd2 ;;
    *) default ;;
esac

# Trap signals
trap 'cleanup' EXIT
trap 'echo interrupted' INT

# Process substitution
diff <(cmd1) <(cmd2)
```
