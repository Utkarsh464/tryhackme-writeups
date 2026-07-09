# Burp Suite: The Basics

## Room Information
- **URL**: https://tryhackme.com/room/burpsuitebasics
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

## Description

Burp Suite: The Basics introduces learners to Burp Suite, the industry-standard platform for web application security testing. Developed by PortSwigger, Burp Suite is used by penetration testers, bug bounty hunters, and security researchers worldwide to intercept, inspect, and modify web traffic. This room focuses on the Community Edition (free version) and covers the essential features needed for effective web application testing. Learners begin by configuring their browser to route traffic through Burp Suite's intercepting proxy, which sits between the browser and the target server. Once configured, all HTTP and HTTPS traffic is visible in Burp Suite, allowing users to pause requests, examine their structure, modify headers and parameters, and forward them to the server. The room covers the Proxy tab, including the Intercept sub-tab for real-time traffic manipulation, HTTP history for reviewing past requests, and WebSockets history for real-time communication analysis. The Repeater tool is introduced for resending and manually modifying individual requests, which is essential for testing how a server responds to different input values. The Intruder tool is covered for automated parameter fuzzing and brute-force attacks against login forms, API endpoints, and parameters. The Decoder module provides functionality for decoding and encoding data in various formats (Base64, URL, Hex, HTML, ASCII). Learners also explore the Target tab for site mapping and the Scope feature for focusing on specific targets. Practical exercises include intercepting a login request, modifying parameters in Repeater, and performing a basic brute-force attack with Intruder.

## Objectives
- Configure browser proxy settings to route traffic through Burp Suite
- Intercept, inspect, and modify HTTP/HTTPS requests and responses
- Use Repeater to manually test parameter variations
- Use Intruder for automated fuzzing and brute-force attacks
- Use Decoder for encoding and decoding data
- Understand site mapping and scope configuration

## Tools
- Burp Suite Community Edition
- Burp Suite Professional (mentioned for advanced features)
- FoxyProxy browser extension (recommended for proxy management)

## Concepts
- Intercepting proxy architecture
- Request modification and replay
- Automated parameter fuzzing
- Payload positions and payload types
- Site mapping and scope control
- Encoding and decoding techniques
