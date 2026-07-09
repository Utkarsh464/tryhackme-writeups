# Bash Cheat Sheet

## Variables
| Syntax | Description |
|--------|-------------|
| `var=value` | Assign (no spaces around `=`) |
| `$var` | Reference value |
| `"$var"` | Quoted (preserves spaces) |
| `${var:-default}` | Use default if unset |
| `export var=value` | Environment variable |
| `local var=val` | Local scope (inside function) |

## Conditionals
| Syntax | Description |
|--------|-------------|
| `if [[ $var == "x" ]]; then` | String comparison |
| `if [[ $var -eq 5 ]]; then` | Integer comparison |
| `if [[ -f file ]]; then` | File exists |
| `if [[ -d dir ]]; then` | Directory exists |
| `if [[ -z "$var" ]]; then` | Variable is empty |
| `if [[ -n "$var" ]]; then` | Variable is not empty |
| `&&` | AND |
| `\|\|` | OR |
| `!` | NOT |

## Loops
| Syntax | Description |
|--------|-------------|
| `for i in list; do ... done` | For loop |
| `for ((i=0; i<5; i++)); do ... done` | C-style for |
| `while condition; do ... done` | While loop |
| `until condition; do ... done` | Until loop |
| `break` | Exit loop |
| `continue` | Skip to next iteration |

## Functions
| Syntax | Description |
|--------|-------------|
| `func() { ... }` | Define function |
| `function func { ... }` | Alternative definition |
| `func arg1 arg2` | Call function |
| `$1`, `$2`, ... | Positional parameters |
| `$@` | All arguments |
| `$#` | Argument count |
| `return N` | Return code |

## Special Variables
| Variable | Description |
|----------|-------------|
| `$0` | Script name |
| `$?` | Last exit code |
| `$$` | Current PID |
| `$!` | Last background PID |
| `$@` | All args |
| `$#` | Arg count |
| `$HOME` | Home directory |
| `$PATH` | Executable search paths |
| `$RANDOM` | Random number 0–32767 |