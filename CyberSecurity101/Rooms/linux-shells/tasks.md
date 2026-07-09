# Tasks: Linux Shells

## Task 1: Shell Fundamentals

**Purpose:** Understand the Bash shell environment and its configuration.

**Skills:** Shell environment, configuration.

**Theory:** The Bash shell is the default on most Linux distributions. It reads configuration files on startup: .bashrc for interactive non-login shells, .bash_profile or .profile for login shells, and .bash_logout on exit. Environment variables like PATH, HOME, USER, and SHELL define the shell environment. Export makes variables available to child processes.

**Commands:**
- echo $VARIABLE - Display variable value
- export - Set environment variable
- env - Display all environment variables
- set - Display shell variables
- alias - Create command alias
- unalias - Remove alias
- source - Execute script in current shell

---

## Task 2: Input-Output Redirection

**Purpose:** Control command input and output using redirection operators.

**Skills:** I/O redirection, data flow control.

**Theory:** Every command has three standard I/O streams: stdin (0), stdout (1), and stderr (2). Redirection operators send output to files (>, >>), read input from files (<), redirect errors (2>), or merge streams (2>&1). Here documents (<<) provide inline input. Understanding redirection is essential for scripting and data processing.

**Commands:**
- command > file - Redirect stdout to file (overwrite)
- command >> file - Redirect stdout to file (append)
- command 2> file - Redirect stderr to file
- command &> file - Redirect both to file
- command < file - Read stdin from file
- command1 | command2 - Pipe output to next command
- tee - Send output to file and stdout

---

## Task 3: Job Control

**Purpose:** Manage multiple processes with job control.

**Skills:** Process management, multitasking.

**Theory:** Job control allows running multiple commands in the same terminal. Background jobs (&) run without blocking the terminal. Ctrl+Z suspends the foreground job. bg resumes a suspended job in the background, and fg brings it to the foreground. jobs lists active jobs. disown removes a job from the shell's job table.

**Commands:**
- command & - Run in background
- jobs - List background jobs
- bg - Resume job in background
- fg - Bring job to foreground
- Ctrl+Z - Suspend foreground job
- disown - Remove job from shell
- nohup - Run immune to hangups

---

## Task 4: Shell Scripting with Variables and Conditionals

**Purpose:** Write shell scripts with variables and conditional logic.

**Skills:** Scripting fundamentals.

**Theory:** Shell scripts use variables without type declaration. Command substitution ($() or backticks) captures command output. Conditionals use if, elif, else, and case with test commands ([ ]) or the newer [[ ]] syntax. String comparisons use = and !=. Numeric comparisons use -eq, -ne, -lt, -le, -gt, -ge. File tests check existence (-f, -d, -e, -s).

**Commands:**
- Variable=value - Assign variable
- $variable or ${variable} - Use variable value
- $(command) - Command substitution
- if [ condition ] - Conditional
- case $var in - Pattern matching
- test - Evaluate expression
- [[ expression ]] - Extended test

---

## Task 5: Loops, Functions, and Error Handling

**Purpose:** Implement loops, functions, and error handling in scripts.

**Skills:** Advanced scripting.

**Theory:** Loops iterate over items or while conditions are true. for loops iterate over lists, while loops run while a condition holds, and until loops run until a condition becomes true. Functions group commands for reuse. Error handling uses exit codes (0 for success, non-zero for failure), the trap command for signals, and set -e for exit on error.

**Commands:**
- for var in list - Iterate over list
- while [ condition ] - Loop while true
- until [ condition ] - Loop until true
- function name { } - Define function
- return - Exit function
- exit - Exit script with code
- trap - Catch signals
- set -e - Exit on error
- set -x - Debug mode
