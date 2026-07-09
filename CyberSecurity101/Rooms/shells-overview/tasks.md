# Shells Overview - Tasks

## Task 1: Introduction to Shells
- Understand what a shell is in the context of penetration testing
- Learn the difference between interactive shells and non-interactive shells
- Understand why shell access is the goal of many exploitation attempts

## Task 2: Reverse Shells
- Understand how reverse shells work (target connects to attacker)
- Identify scenarios where reverse shells are preferred
- Set up a netcat listener on the attacker machine
- Execute a reverse shell payload on the target
- Observe the connection establishment and shell interaction

## Task 3: Bind Shells
- Understand how bind shells work (attacker connects to target)
- Identify scenarios where bind shells are preferred
- Execute a bind shell payload on the target
- Connect to the bind shell from the attacker machine
- Understand the limitations and risks of bind shells

## Task 4: Web Shells
- Understand what web shells are and how they differ from network shells
- Write a simple PHP web shell
- Deploy the web shell on a web server
- Interact with the web shell through a browser
- Understand the limitations (HTTP latency, command parsing)

## Task 5: Generating Payloads with msfvenom
- Learn the msfvenom syntax for payload generation
- List available payloads with msfvenom -l payloads
- Generate a Linux reverse shell payload
- Generate a Windows reverse shell payload
- Understand the difference between staged and stageless payloads

## Task 6: Staged vs Stageless Payloads
- Understand staged payloads (small stub fetches larger payload)
- Understand stageless payloads (complete payload in one connection)
- Compare the size, reliability, and detection characteristics
- Choose the appropriate type for different scenarios

## Task 7: Netcat Listeners
- Set up a basic netcat listener: nc -lvnp 4444
- Understand the flags: -l (listen), -v (verbose), -n (no DNS), -p (port)
- Configure persistent listeners for multiple connections
- Use rlwrap with netcat for better shell interaction

## Task 8: Metasploit Multi-Handler
- Use Metasploit's exploit/multi/handler for advanced listener management
- Configure payload options to match the generated payload
- Handle staged payloads automatically
- Understand post-exploitation module integration

## Task 9: Shell Stabilisation and TTY Upgrades
- Understand why default shells are limited (no tab completion, no job control)
- Use Python PTY module for TTY upgrade
- Use socat for full TTY terminal
- Use the script command for TTY upgrade
- Set proper terminal environment variables (TERM, SHELL)

## Task 10: Firewall and Network Considerations
- Understand how firewalls affect shell connections
- Learn about egress filtering and its impact on reverse shells
- Learn about ingress filtering and its impact on bind shells
- Explore techniques for bypassing network restrictions
- Use alternative ports and protocols for evasion

## Task 11: Practical Challenge
- Set up a complete shell scenario from exploitation to interaction
- Generate appropriate payload for the target
- Configure the listener and catch the shell
- Upgrade the shell to a fully interactive TTY
- Document the process and findings
