# Hydra - Tasks

## Task 1: Introduction to Hydra
- Understand what Hydra is and its role in penetration testing
- Learn about the supported protocols and attack types
- Understand the difference between online and offline brute-force attacks

## Task 2: Installing Hydra
- Install Hydra using the package manager (apt, brew, etc.)
- Verify the installation with `hydra --help`
- Understand the basic command-line structure

## Task 3: Understanding Hydra Syntax
- Learn the basic syntax: `hydra -l username -P wordlist.txt service://target`
- Understand the difference between -l (single username) and -L (username list)
- Understand the difference between -p (single password) and -P (password list)
- Learn about the -t flag for parallel tasks and -v for verbose output

## Task 4: HTTP GET Form Brute-Force
- Identify a login form that uses GET parameters
- Construct a Hydra command targeting HTTP GET authentication
- Specify the failure condition string with the -f flag
- Analyze the results to find valid credentials

## Task 5: HTTP POST Form Brute-Force
- Use browser developer tools or curl to analyze a POST login form
- Identify the form parameter names (username, password, csrf_token, etc.)
- Craft the Hydra command with the http-post-form module
- Specify the form parameters, failure string, and optional headers
- Execute the attack and interpret results

## Task 6: SSH Brute-Force
- Understand SSH authentication and how Hydra interacts with it
- Perform a brute-force attack against SSH with a username list
- Use the -t flag to control connection concurrency
- Handle rate limiting and connection timeouts

## Task 7: FTP Brute-Force
- Understand FTP authentication mechanisms
- Perform a brute-force attack against an FTP server
- Understand the difference between anonymous FTP and authenticated FTP
- Apply Hydra's ftp module for directory attacks

## Task 8: Advanced Hydra Options
- Use the -s flag to specify a non-standard port
- Use the -o flag to save results to a file
- Use the -w and -W flags for timing control
- Use protocol-specific options (e.g., :// for service paths)

## Task 9: Wordlists and Password Generation
- Understand common password wordlist sources (rockyou, SecLists, crackstation)
- Learn where to find wordlists on the system (/usr/share/wordlists/)
- Use Hydra's -x flag for brute-force generation (character sets, lengths)
- Combine wordlists with rules for more effective attacks

## Task 10: Defensive Measures
- Understand account lockout policies and how they affect brute-forcing
- Learn about CAPTCHA and rate limiting as countermeasures
- Explore fail2ban and similar intrusion prevention tools
- Understand logging and monitoring for brute-force detection
- Discuss ethical use and authorization requirements

## Task 11: Practical Challenge
- Apply all learned techniques in a simulated environment
- Brute-force multiple services with different configurations
- Analyze results and report findings
- Review the impact and remediation recommendations
