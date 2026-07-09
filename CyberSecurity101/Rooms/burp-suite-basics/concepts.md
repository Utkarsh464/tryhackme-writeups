# Burp Suite: The Basics - Concepts

## Intercepting Proxy
An intercepting proxy sits between the client (browser) and the target server, capturing all traffic passing through it. When properly configured, the proxy can pause requests and responses, allowing the user to inspect and modify them before they reach their destination. This capability is fundamental to web application security testing because it allows testers to bypass client-side controls, manipulate parameters that are not exposed in the UI, and observe the raw communication between browser and server. The proxy must decrypt HTTPS traffic using a self-signed CA certificate installed in the browser's trust store.

## Request Modification
The ability to modify HTTP requests in transit is the core value of an intercepting proxy. Security testers can change form field values, modify hidden fields, alter cookies, add or remove headers, change HTTP methods, and inject payloads. Common testing scenarios include modifying a price field in a shopping cart request, changing a user ID parameter to access another user's data, bypassing client-side input validation, and testing for injection vulnerabilities. Response modification is also possible, which can be used to test how the client-side application handles unexpected server responses.

## Payload Positions and Attack Types
Intruder uses payload positions, marked with section signs (), to identify where payloads should be inserted into a request. The attack type determines how payloads are applied across multiple positions. Sniper is the most common type, testing each position individually with all payloads. Battering ram is useful when the same value must appear in multiple positions (e.g., same username and password). Pitchfork matches corresponding entries from multiple lists (e.g., username list and password list paired by position). Cluster bomb tests all combinations, which is computationally expensive but thorough for small payload sets.

## Session Handling and Scope
Proper scope configuration ensures that Burp Suite only captures and processes traffic relevant to the target application. Scope can be defined by URL protocol, host, port, and file path. Traffic outside the scope can be forwarded automatically without interception, reducing noise and improving performance. Session handling rules allow Burp Suite to maintain session state across multiple requests, automatically responding to challenges, CSRF tokens, and login requirements. Understanding scope and session handling is essential for efficient testing of complex, multi-step web applications.

## Encoding and Decoding
Web applications use various encoding schemes for data transmission and storage. URL encoding (percent encoding) is used to represent unsafe ASCII characters in URLs. Base64 encoding is commonly used to transmit binary data in text-based protocols. HTML entities encode special characters for safe display in HTML. Understanding encoding is crucial for both exploiting and mitigating injection attacks. The Decoder tool can also chain multiple encoding/decoding operations, which is useful for analyzing nested encoding commonly used to evade security filters.

## WebSocket Interception
WebSockets provide full-duplex communication channels over a single TCP connection, commonly used for real-time features like chat, notifications, and live updates. Burp Suite can intercept and modify WebSocket messages, allowing testers to manipulate real-time data flows. This capability is increasingly important as more web applications adopt WebSockets for interactive features. The WebSockets history tab in the Proxy records all WebSocket messages, and they can be sent to Repeater for manual testing.
