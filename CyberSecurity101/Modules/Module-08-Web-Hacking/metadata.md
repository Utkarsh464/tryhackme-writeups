# Module 08: Web Hacking

## Overview

Web Hacking is a foundational module in the Cyber Security 101 learning path that introduces learners to the core concepts of web application security. As web applications have become the primary interface for businesses, services, and communication, understanding how to assess and exploit their vulnerabilities is an essential skill for any security professional. This module bridges the gap between general networking knowledge and practical offensive security techniques focused on the web.

The module begins with Web Application Basics, which covers the fundamental architecture of web applications, including the HTTP/HTTPS protocol, request-response cycles, status codes, headers, cookies, and session management. Learners gain an understanding of how the client-server model operates and how data flows between browsers and servers. This foundation is critical before diving into more advanced topics.

JavaScript Essentials introduces the client-side scripting language that powers modern web interactivity. Understanding JavaScript is crucial for web security because many attacks, such as Cross-Site Scripting (XSS), exploit poorly handled JavaScript code. Learners explore variables, functions, DOM manipulation, event handling, and asynchronous programming. This room also covers how JavaScript interacts with browser security mechanisms like the Same-Origin Policy.

SQL Fundamentals teaches the language used to interact with relational databases. SQL injection remains one of the most prevalent and dangerous web vulnerabilities. This room covers SELECT, INSERT, UPDATE, DELETE queries, JOIN operations, and database structure. Learners practice writing queries and understand how unsanitized user input can lead to database compromise.

Burp Suite: The Basics introduces the industry-standard web application security testing tool. Burp Suite is used by penetration testers and bug bounty hunters worldwide. This room covers proxy configuration, intercepting requests, modifying traffic, repeater functionality, and an introduction to intruder attacks. Learners gain hands-on experience with web traffic manipulation.

The module culminates with OWASP Top 10 - 2021, which covers the most critical web application security risks as defined by the Open Web Application Security Project. This room covers Broken Access Control, Cryptographic Failures, Injection, Insecure Design, Security Misconfiguration, Vulnerable and Outdated Components, Identification and Authentication Failures, Software and Data Integrity Failures, Security Logging and Monitoring Failures, and Server-Side Request Forgery (SSRF). Each vulnerability is explained with real-world examples and mitigation strategies.

By the end of this module, learners will have a solid understanding of web application architecture, common vulnerabilities, and the tools used to identify and exploit them. This knowledge serves as a stepping stone to more advanced web security topics and bug bounty hunting.

## Rooms

1. **Web Application Basics** (Free, ~1 hour)
2. **JavaScript Essentials** (Premium, ~1 hour)
3. **SQL Fundamentals** (Premium, ~1 hour)
4. **Burp Suite: The Basics** (Premium, ~1 hour)
5. **OWASP Top 10 - 2021** (Free, ~2 hours)

## Prerequisites

- Basic understanding of networking (Module 05)
- Familiarity with Linux command line (Module 02)
- No prior web development experience required

## Learning Objectives

- Understand HTTP/HTTPS protocol and web application architecture
- Identify and exploit common web vulnerabilities
- Use Burp Suite for web application testing
- Recognize OWASP Top 10 vulnerabilities
- Understand client-side and server-side attack surfaces
