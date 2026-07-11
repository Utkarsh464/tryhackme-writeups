# OWASP Top 10 - 2025 — Tools

## Burp Suite Community Edition
- **Description:** The industry-standard web application security testing framework. The free community edition includes an intercepting proxy, repeater, intruder (rate-limited), decoder, and comparer. Used for inspecting and modifying HTTP/HTTPS traffic between the browser and target application.
- **Website:** https://portswigger.net/burp/communitydownload
- **Key Features:** Intercepting proxy for traffic inspection and modification, Repeater for resending and modifying individual requests, Intruder for brute forcing and fuzzing (throttled in community edition), Decoder for encoding/decoding data, and Comparer for diffing responses.

## SQLMap
- **Description:** An open-source penetration testing tool that automates the detection and exploitation of SQL injection vulnerabilities. It supports a wide range of database backends (MySQL, PostgreSQL, MSSQL, Oracle, SQLite) and injection techniques (UNION-based, error-based, blind, time-based, out-of-band).
- **Repository:** https://github.com/sqlmapproject/sqlmap
- **Key Features:** Automatic detection of injection points, database fingerprinting, data extraction, OS command execution via SQL, integration with Burp Suite, and support for HTTP proxies and authentication.

## OWASP Dependency-Check
- **Description:** A tool that identifies known vulnerabilities in project dependencies by checking them against the National Vulnerability Database (NVD). Available as a CLI tool, Maven plugin, Gradle plugin, and Jenkins plugin.
- **Website:** https://owasp.org/www-project-dependency-check/
- **Key Features:** Supports Java, .NET, Python, Ruby, Node.js, and C/C++ projects, generates HTML and JSON reports, and integrates into CI/CD pipelines.

## jwt_tool
- **Description:** A toolkit for testing JSON Web Token (JWT) security. Capable of inspecting tokens, testing for common vulnerabilities (none algorithm, weak HMAC secret, algorithm confusion), and forging valid tokens.
- **Repository:** https://github.com/ticarpi/jwt_tool
- **Key Features:** Token decoding, signature verification, automated scanning for JWKS injection, timing attacks, and key confusion.

## Gobuster
- **Description:** A command-line tool for brute forcing URIs (directories and files), DNS subdomains, and virtual host names. Useful for discovering hidden resources during web application reconnaissance.
- **Repository:** https://github.com/OJ/gobuster
- **Key Features:** Multi-threaded scanning, support for multiple wordlist formats, directory/file enumeration, DNS subdomain enumeration, and vhost enumeration.
