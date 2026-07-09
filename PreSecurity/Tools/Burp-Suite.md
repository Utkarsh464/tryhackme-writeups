# Burp Suite

## Purpose
Web application security testing platform. Intercepts HTTP/S traffic between browser and server for manual testing, scanning, and exploitation.

## Installation
- Community Edition: https://portswigger.net/burp/communitydownload
- Pre-installed on Kali Linux

## Basic Usage
1. Start Burp → Proxy tab → Intercept Off
2. Set browser proxy to `127.0.0.1:8080`
3. Browse to target — requests appear in Proxy → HTTP History
4. Turn Intercept On to pause/modify requests
5. Send interesting requests to Repeater, Intruder, or Scanner

## Important Commands
- **Proxy tab** - Intercept, forward, drop requests
- **Repeater** - Send modified requests repeatedly and view responses
- **Intruder** — Brute-force, fuzzing, parameter enumeration
- **Decoder** — URL, Base64, hex encode/decode
- **Sequencer** — Token randomness analysis
- **Extender** — Add BApp Store extensions
- `Ctrl+R` — Send to Repeater
- `Ctrl+I` — Send to Intruder
- **Target Scope** — Restrict Burp to specific hosts

## Typical Workflow
1. Configure browser proxy → CA cert install
2. Browse application, map endpoints
3. Test interesting requests in Repeater
4. Use Intruder for parameter fuzzing/auth bypass
5. Scan with Burp Scanner (Pro) or manual testing
6. Exploit with Repeater or browser integration

## Official Documentation
https://portswigger.net/burp/documentation