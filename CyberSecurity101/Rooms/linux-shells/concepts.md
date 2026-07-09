# Concepts: Linux Shells

## 1. Shell
A command-line interpreter that provides a user interface for accessing operating system services. The shell accepts human-readable commands, translates them into system calls, and displays results. Shells also provide scripting capabilities for automation. Common Linux shells include Bash, Zsh, Fish, and Ksh.

## 2. Bash (Bourne Again SHell)
The default shell on most Linux distributions and the primary focus of this room. Bash is an enhanced version of the original Bourne shell (sh) with additional features including command history, tab completion, job control, aliases, functions, and advanced scripting capabilities.

## 3. Shell Environment
The context in which the shell operates, defined by environment variables, shell variables, aliases, functions, and shell options. Environment variables are inherited by child processes and affect program behavior. The environment is configured through startup files like .bashrc and .bash_profile.

## 4. Interactive vs. Non-Interactive Shells
Interactive shells read commands from the user via a terminal. Non-interactive shells run scripts or commands automatically. Startup files are loaded differently depending on whether the shell is interactive or non-interactive, and whether it is a login shell.

## 5. Login vs. Non-Login Shells
Login shells are started with the --login flag or when logging into a system (SSH, TTY). They read .bash_profile, .bash_login, or .profile. Non-login shells are started from within a logged-in session. They read .bashrc. Understanding this distinction is important for shell customization.

## 6. Standard Streams
Three data channels connected to every process: stdin (file descriptor 0, standard input) receives input, stdout (file descriptor 1, standard output) displays normal output, and stderr (file descriptor 2, standard error) displays error messages. Redirection allows control over these streams.

## 7. Exit Codes
Numeric values returned by commands and scripts to indicate success or failure. An exit code of 0 means success, while non-zero codes indicate various error conditions. Exit codes are checked with $? immediately after command execution or used in conditional statements for flow control.

## 8. Job Control
The ability to manage multiple processes within a single shell session. Jobs can be run in the background (using &), suspended (Ctrl+Z), resumed in the background (bg) or foreground (fg), and monitored (jobs). Job control is essential for managing long-running tasks in interactive sessions.

## 9. Command Substitution
A technique that captures the output of a command and uses it as part of another command. The modern syntax $(command) is preferred over the older backtick syntax. Command substitution enables dynamic command construction and data processing.

## 10. Parameter Expansion
A powerful feature in Bash that transforms variable values during expansion. Common parameter expansions include ${var:-default} (default value), ${var:offset:length} (substring), ${var#pattern} (remove prefix), ${var%pattern} (remove suffix), and ${var/old/new} (search and replace).

## 11. Here Documents and Here Strings
Redirection features for providing inline input. Here documents (<< EOF ... EOF) pass multiple lines of input to a command. Here strings (<<< "text") pass a single string as stdin. Both are useful for scripting and automation.

## 12. Shell Customization
Modifying the shell's behavior and appearance through configuration files. Users customize their prompt (PS1 variable), create aliases for common commands, set environment variables, define functions, and configure tab completion. Changes are typically added to ~/.bashrc for interactive shells.
