# Burp Suite

## Purpose
Burp Suite is an integrated platform for performing security testing of web applications. Developed by PortSwigger, it provides a comprehensive set of tools including an intercepting proxy, vulnerability scanner, repeater, intruder, decoder, and sequencer. Burp Suite is the industry standard for web application penetration testing, used to identify vulnerabilities such as SQL injection, XSS, CSRF, and authentication flaws.

## Installation
Burp Suite Community Edition is free and available for download. The Professional edition requires a paid license.
```bash
# Download from PortSwigger (Java-based, cross-platform)
# Community Edition:
wget https://portswigger.net/burp/releases/download?product=community&type=linux
chmod +x burpsuite_community_linux.sh
./burpsuite_community_linux.sh

# Alternative: Install via package manager
# Kali Linux (pre-installed)
sudo apt install burpsuite

# Using bbeastie (Arch Linux AUR)
yay -S burpsuite
```

## Basic Usage
1. Launch Burp Suite and create a temporary project (Community) or saved project (Professional)
2. Configure browser proxy to `127.0.0.1:8080`
3. Install Burp's CA certificate for HTTPS interception
4. Navigate to the Target tab to define scope
5. Enable intercept in the Proxy tab to capture requests/replies
6. Send interesting requests to Repeater, Intruder, or Scanner

## Important Tools
- **Proxy** - Intercepts HTTP/HTTPS traffic between browser and server. Allows modification of requests before forwarding. Includes WebSocket interception.
- **Repeater** - Manually craft and resend individual HTTP requests. Modify parameters, headers, and body to test for vulnerabilities. Supports multiple tabs for parallel testing.
- **Intruder** - Automated parameter fuzzing tool. Supports four attack types: Sniper (single payload), Battering Ram (same payload in multiple positions), Pitchfork (parallel payloads), and Cluster Bomb (cross-product payloads).
- **Scanner** (Professional only) - Automated vulnerability scanning with both active and passive crawling. Identifies common web vulnerabilities with detailed advisory reports.
- **Decoder** - URL, Base64, Hex, HTML, and other encoding/decoding operations. Includes smart decode and hash identification.
- **Sequencer** - Analyzes the randomness of session tokens and CSRF tokens using statistical analysis (FIPS 140-2 compliant tests).
- **Extender** - Allows installation of community-developed BApp Store extensions. Popular extensions include Autorize, JSON Web Tokens, and Collaborator Everywhere.
- **Inspector** - Visual HTTP request editor showing decoded values, parameters, cookies, and JSON/XML hierarchy.

## Typical Workflow
1. Browse the target application with proxy enabled to map functionality
2. Set scope to focus on the target domain
3. Review HTTP history for interesting requests and parameters
4. Send suspicious requests to Intruder for parameter fuzzing
5. Use Repeater to manually test injection points
6. Analyze responses for error messages, timing differences, and reflection
7. Use Decoder to process encoded data and hashes
8. (Professional) Run active scanner on discovered endpoints
9. Document findings with evidence from Repeater responses

## Advantages
- Comprehensive all-in-one web testing platform
- Intuitive GUI with well-organized workflow
- Extensive BApp Store ecosystem for extending functionality
- Powerful Intruder engine for brute-force and fuzzing
- Collaborator integration for out-of-band vulnerability detection
- Detailed reporting (Professional) with severity ratings

## Limitations
- Professional edition is expensive ($449/year)
- Community edition lacks scanner, has rate-limited Intruder
- Java-based application can be resource-intensive
- Learning curve for advanced features
- Interception slows down browsing significantly
- Requires manual configuration for complex authentication flows

## Industry Use
Burp Suite is the de facto standard for web application security testing. Used by penetration testers, bug bounty hunters, and security auditors. PortSwigger's Web Security Academy provides free training materials. Many organizations mandate Burp Suite Professional as the primary web testing tool.

## Official Documentation
- Official Site: https://portswigger.net/burp
- Documentation: https://portswigger.net/burp/documentation
- Web Security Academy: https://portswigger.net/web-security
- BApp Store: https://portswigger.net/bappstore
- GitHub: https://github.com/PortSwigger
