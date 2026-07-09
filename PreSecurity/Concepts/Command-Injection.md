# Command Injection

## Definition
OS Command Injection is a web vulnerability where an attacker can execute arbitrary operating system commands on the server through a vulnerable application. It occurs when user input is passed unsanitized to system shells (e.g., `system()`, `exec()`, `subprocess`). Attackers use shell metacharacters (`;`, `|`, `&&`, `$()`, backticks) to chain or substitute commands.

## Why It Matters
Command injection can lead to complete server compromise. Unlike file inclusion or SQLi, it provides direct OS-level access. It appears frequently in web applications that invoke system commands for file operations, network diagnostics, or media processing.

## Where It Appears in the Path
- Web Hacking Fundamentals

## Prerequisites
- Linux command line, HTTP basics

## Key Points
- Blind vs. out-of-band detection: use `ping`, `sleep`, or DNS exfiltration
- Common injection points: forms, headers (User-Agent, Cookie), file names
- Filter bypass: use `$IFS` for spaces, hex encoding, base64
- Prevention: use language-native APIs, never shell out with unsanitized input

## Common Interview Questions
1. How do you test for command injection?
**Answer:** Inject `; sleep 5` or `| whoami` and observe timing or output.
2. What characters are used for injection?
**Answer:** `;`, `|`, `&&`, `||`, `$()`, `` ` ``, `%0a` (newline).
3. How do you prevent command injection?
**Answer:** Avoid shell calls; use parameterized APIs; validate/whitelist input.

## Further Reading
- OWASP Command Injection
- PortSwigger Web Security Academy