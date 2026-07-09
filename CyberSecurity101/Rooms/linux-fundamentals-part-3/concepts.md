# Concepts: Linux Fundamentals Part 3

## 1. Shell Scripting
Writing sequences of shell commands in a file for automated execution. Shell scripts automate repetitive tasks, process data, and create tools. Scripts use variables, conditionals, loops, and functions to implement logic. The shebang line (#!/bin/bash) tells the system which interpreter to use.

## 2. Shebang (#!)
A special comment at the beginning of a script file that specifies the interpreter to execute the script. For Bash scripts, the shebang is #!/bin/bash. Other interpreters include #!/bin/sh (POSIX shell), #!/usr/bin/python3 (Python), and #!/usr/bin/env node (Node.js).

## 3. Variables
Named storage locations for data in shell scripts. Variables are assigned without the $ prefix (NAME="value") and accessed with the $ prefix ($NAME or ${NAME}). Environment variables are available to child processes. Local variables are script-scoped.

## 4. Command Substitution
A technique for capturing the output of a command into a variable. The modern syntax is $(command), which allows nesting and is preferred over the older backtick syntax (command).

## 5. Input-Output Redirection
Controlling where command input comes from and where output goes. Redirection operators send output to files, read input from files, and merge data streams. This enables complex data processing pipelines and logging.

## 6. Pipes
A mechanism for connecting the stdout of one command to the stdin of another command using the pipe operator (|). Pipes enable command chaining for powerful data processing without intermediate files.

## 7. Conditional Statements
Programming constructs that execute different code paths based on conditions. The if statement evaluates a condition and executes the corresponding block. The case statement matches patterns for multi-way branching. Test conditions check file attributes, string comparisons, and numeric comparisons.

## 8. Loops
Constructs for repeating code blocks. The for loop iterates over a list of items. The while loop executes while a condition is true. The until loop executes until a condition becomes true.

## 9. Functions
Reusable blocks of code within scripts. Functions accept arguments ($1, $2, etc.), return values (return command), and can be defined before use. Functions reduce code duplication and improve script organization.

## 10. Package Management
The process of installing, updating, configuring, and removing software packages. Package managers handle dependencies, resolve conflicts, and maintain package databases. Different Linux distributions use different package managers (apt for Debian/Ubuntu, yum/dnf for RHEL/CentOS).

## 11. Cron
A time-based job scheduler in Unix-like systems that executes tasks at specified times or intervals. Cron jobs are defined in crontab files with five time fields (minute, hour, day of month, month, day of week) followed by the command to execute.

## 12. SSH (Secure Shell)
A cryptographic network protocol for secure remote access to systems over an unsecured network. SSH provides encrypted communication, authentication, and data integrity. It is the primary method for remote server administration in Linux environments.
