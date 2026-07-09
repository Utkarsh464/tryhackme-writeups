# Concepts: Windows Command Line

## 1. Command Prompt (cmd.exe)
The traditional Windows command-line interpreter, providing a text-based interface for executing commands and batch scripts. cmd.exe is a legacy component from the MS-DOS era but remains an essential tool for system administration, troubleshooting, and automation in Windows environments.

## 2. Command Interpreter
A program that reads user input as commands, parses them, and executes the corresponding programs or built-in functions. The command interpreter provides features like command history (F7), tab completion, environment variable expansion (%VAR%), and batch file processing.

## 3. Environment Variables
Named values that store system and user configuration information accessible to all command-line processes. Common variables include %PATH% (executable search directories), %SYSTEMROOT% (Windows directory), %TEMP% (temporary files location), %USERNAME% (current user), and %COMPUTERNAME% (machine name).

## 4. Batch Scripting
Creating text files with .bat or .cmd extensions containing sequences of commands executed in order. Batch scripts support variables (set), conditionals (if, if exist, if errorlevel), loops (for), labels (goto), and subroutines (call). They are used for automation of repetitive tasks.

## 5. Error Levels
Exit codes returned by commands and programs to indicate success or failure. An error level of 0 typically indicates success, while non-zero values indicate specific errors. The if errorlevel command checks these codes for conditional execution in batch scripts.

## 6. Standard Streams
Input and output channels for command-line programs. stdin (standard input, handle 0) receives input, stdout (standard output, handle 1) displays normal output, and stderr (standard error, handle 2) displays error messages. Redirection operators direct these streams.

## 7. Redirection Operators
Symbols that control input and output streams. > redirects output to a file (overwrite), >> appends output to a file, < reads input from a file, 2> redirects errors, 2>&1 merges error into output stream, and | pipes output to another command.

## 8. Network Diagnostics
Command-line tools for troubleshooting network connectivity. ipconfig shows IP configuration, ping tests reachability, tracert traces network routes, nslookup resolves DNS names, netstat displays active connections and listening ports, and pathping combines ping and tracert with latency analysis.

## 9. Process Management
Commands for monitoring and controlling running processes. tasklist displays running processes with PID, memory usage, and session information. taskkill terminates processes by PID or image name with optional force (/F) flag.

## 10. File Attributes
Metadata properties associated with files and directories in Windows. Attributes include Read-only (R), Hidden (H), System (S), Archive (A), and Indexed (I). The attrib command displays and modifies file attributes. Hidden and system files are hidden by default in File Explorer.
