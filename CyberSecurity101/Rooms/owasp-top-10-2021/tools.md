# OWASP Top 10 - 2021 - Tools

## Burp Suite Community Edition
Burp Suite is the primary tool used throughout this room for intercepting and modifying web traffic. For OWASP Top 10 testing, key features include: Proxy for capturing login forms and API requests to test authentication and access control; Repeater for manually testing parameter manipulation (IDOR, injection); Intruder for fuzzing parameters with SQL injection payloads, brute-forcing authentication, and enumerating accessible resources; and Decoder for analyzing encoded data and cryptographic failures. Burp Suite's ability to intercept, modify, and replay requests makes it the most versatile tool for exploring all ten categories.

## curl
curl is used extensively for command-line testing, particularly for scripting and automation. It is useful for testing IDOR vulnerabilities by sending requests with modified parameters, testing injection points with crafted payloads, examining response headers for security misconfigurations, and testing SSRF by observing how the server handles various URL inputs. curl's verbosity flags (-v) reveal request and response details, and its ability to handle cookies (-b, -c) makes it useful for session-based testing. The --resolve flag can be used to direct requests to specific IP addresses for SSRF testing.

## Browser Developer Tools
Browser developer tools are essential for analyzing client-side security issues. The Network tab reveals all HTTP requests initiated by the page, including API calls that may not be visible in the UI. The Sources tab shows all client-side JavaScript, which can be analyzed for authentication logic flaws, insecure deserialization, and hardcoded secrets. The Application tab displays cookies, localStorage, and sessionStorage, which can reveal session management weaknesses. The Elements tab shows the DOM, including hidden form fields that may contain sensitive data or control access decisions.

## Online Vulnerability Databases
Understanding the OWASP Top 10 requires familiarity with vulnerability databases: the National Vulnerability Database (NVD) at nvd.nist.gov provides detailed information on CVEs; CVE MITRE at cve.mitre.org is the authoritative CVE list; OWASP's own website provides detailed cheat sheets for each vulnerability category; and Exploit-DB maintains a public database of proof-of-concept exploits. These resources are essential for understanding how real-world vulnerabilities are classified, reported, and exploited.

## Automated Scanners (Reference)
While this room focuses on manual testing, automated scanners can quickly identify potential vulnerabilities. Tools like OWASP ZAP (Zed Attack Proxy) provide active and passive scanning capabilities similar to Burp Suite Professional. Nikto is a web server scanner for finding misconfigurations and outdated software. WPScan specializes in WordPress vulnerability scanning. Understanding what automated scanners can detect helps testers focus manual efforts on areas that require human analysis, such as business logic flaws and complex access control vulnerabilities.
