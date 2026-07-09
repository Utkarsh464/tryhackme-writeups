# Burp Suite: The Basics - Tasks

## Task 1: Introduction to Burp Suite
- Understand what Burp Suite is and its role in web security testing
- Differentiate between Community Edition and Professional Edition
- Learn about the Burp Suite architecture and core components

## Task 2: Installing and Configuring Burp Suite
- Download and install Burp Suite Community Edition
- Configure the proxy listener (default 127.0.0.1:8080)
- Install the PortSwigger CA certificate for HTTPS inspection
- Configure FoxyProxy or manual proxy settings in the browser

## Task 3: The Proxy - Intercept Tab
- Understand how the intercepting proxy captures traffic
- Intercept a request and examine its structure
- Modify request parameters, headers, and body
- Forward, drop, and toggle interception on/off
- Understand the difference between intercepting requests and responses

## Task 4: The Proxy - HTTP History
- Review the HTTP history tab to see all captured requests
- Filter history by method, status code, MIME type, and search terms
- Examine request and response details for each entry
- Send interesting requests to Repeater, Intruder, or other tools

## Task 5: The Target Tab and Scope
- Understand the Target tab and site map
- Set the scope to focus on specific targets
- Filter Proxy history to show only in-scope items
- Use the site map to navigate application structure

## Task 6: Repeater
- Send requests from Proxy to Repeater
- Modify request parameters, headers, and body
- Send modified requests and observe responses
- Use the different view options (render, raw, hex)
- Understand the difference between Repeater and browser-based testing

## Task 7: Intruder Basics
- Understand Intruder as an automated fuzzing tool
- Send a request to Intruder and define payload positions
- Choose the appropriate attack type (Sniper, Battering ram, Pitchfork, Cluster bomb)
- Configure a payload set (simple list, numbers, brute force)
- Start an attack and analyze results

## Task 8: Intruder Attack Types
- Use Sniper for single-position testing with multiple payloads
- Use Battering ram for injecting the same payload into multiple positions
- Use Pitchfork for testing multiple payload sets in parallel
- Use Cluster bomb for testing all combinations of multiple payload sets

## Task 9: Decoder
- Encode and decode data in various formats
- Use URL encoding, Base64, Hex, HTML encoding, and ASCII
- Chain multiple encoding/decoding operations
- Use smart decode to automatically detect encoding

## Task 10: Practical Application
- Configure Burp Suite proxy and browser
- Intercept a login request and analyze its structure
- Use Repeater to modify parameters and test server responses
- Use Intruder to perform a basic brute-force attack on a login form
- Analyze results and identify valid credentials

## Task 11: Conclusion and Best Practices
- Review all Burp Suite features covered
- Understand best practices for proxy configuration
- Learn about additional Burp extensions and advanced features
- Prepare for more advanced web application testing
