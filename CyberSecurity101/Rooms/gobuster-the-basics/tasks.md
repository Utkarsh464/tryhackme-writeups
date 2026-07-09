# Gobuster: The Basics - Tasks

## Task 1: Introduction to Gobuster
- Understand what Gobuster is and its role in reconnaissance
- Learn about the three modes of operation
- Compare Gobuster with alternative tools (dirb, dirbuster, ffuf)

## Task 2: Installing Gobuster
- Install Gobuster using apt, brew, or from source
- Verify the installation with `gobuster --help`
- Understand the command-line structure for each mode

## Task 3: Understanding HTTP Status Codes
- Learn what each common status code means for discovery
- 200: Success (resource found and accessible)
- 301/302: Redirect (resource found but redirected)
- 403: Forbidden (resource exists but access denied)
- 404: Not Found (resource does not exist)
- Identify false positives and filter results effectively

## Task 4: Directory and File Enumeration (dir mode)
- Learn the basic syntax: `gobuster dir -u http://target.com -w wordlist.txt`
- Use the -x flag to append file extensions (.php, .txt, .bak, .old)
- Filter results by status code with the -s flag
- Exclude specific status codes with --exclude-status
- Understand the output format and result interpretation

## Task 5: Advanced Directory Options
- Use -n to not follow redirects
- Use -f to append a trailing slash to directories
- Use -r to follow redirects
- Handle cookies with the -c flag
- Set custom headers with the -H flag
- Specify a custom User-Agent with -a

## Task 6: DNS Subdomain Enumeration (dns mode)
- Understand DNS enumeration and its importance
- Learn the basic syntax: `gobuster dns -d example.com -w subdomains.txt`
- Use the -i flag to show IP addresses for resolved subdomains
- Understand wildcard DNS and how to detect it
- Use the --wildcard flag to handle wildcard detection

## Task 7: Advanced DNS Options
- Configure a custom DNS resolver with the -r flag
- Use the -c flag for DNS retries
- Understand how to choose effective subdomain wordlists
- Analyze DNS results to identify interesting subdomains

## Task 8: Virtual Host Enumeration (vhost mode)
- Understand what virtual hosts are and why they matter
- Learn the basic syntax: `gobuster vhost -u http://target.com -w wordlist.txt`
- Understand how vhost enumeration differs from DNS enumeration
- Interpret Content-Length differences in responses
- Handle false positives from default vhost configurations

## Task 9: Wordlist Selection
- Understand the common wordlist locations (/usr/share/wordlists/)
- Learn about SecLists and its directory structure
- Choose appropriate wordlists for different tasks
- Understand the trade-off between wordlist size and scan time

## Task 10: Performance Optimization
- Use the -t flag to control thread count
- Understand how network conditions affect optimal thread count
- Use the -q flag for quiet mode (only show results)
- Use the -o flag to save results to a file for later analysis

## Task 11: Practical Challenge
- Perform a comprehensive reconnaissance on a target
- Use all three modes of Gobuster
- Compile findings and identify attack vectors
- Understand how fits into the broader penetration testing methodology
