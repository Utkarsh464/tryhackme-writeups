# Module 08: Web Hacking - Rooms

## Room 1: Web Application Basics

- **URL**: https://tryhackme.com/room/webapplicationbasics
- **Difficulty**: Easy
- **Subscription**: Free
- **Estimated Time**: ~1 hour

This room introduces the fundamental concepts of web applications. Learners explore the HTTP protocol, including request methods (GET, POST, PUT, DELETE), status codes (200, 301, 403, 404, 500), headers, and cookies. The room covers how web servers and browsers communicate, the role of HTML forms, and session management using cookies and tokens. Hands-on tasks involve inspecting HTTP traffic, understanding URL structures, and manipulating requests to observe server responses. This room is the prerequisite for all subsequent web hacking modules.

## Room 2: JavaScript Essentials

- **URL**: https://tryhackme.com/room/javascriptessentials
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

JavaScript Essentials covers the programming language that powers client-side web interactivity. The room begins with basic syntax, variables, data types, and control flow. It progresses to functions, objects, arrays, and the Document Object Model (DOM). Learners explore event handling, asynchronous programming with callbacks and promises, and the Fetch API for making HTTP requests from the browser. Security topics include the Same-Origin Policy, Content Security Policy (CSP), and how improper JavaScript handling can lead to Cross-Site Scripting (XSS) vulnerabilities.

## Room 3: SQL Fundamentals

- **URL**: https://tryhackme.com/room/sqlfundamentals
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

SQL Fundamentals teaches the Structured Query Language used to interact with relational databases. The room covers creating and querying databases, tables, and records. Learners practice SELECT statements with WHERE clauses, JOIN operations across multiple tables, aggregate functions (COUNT, SUM, AVG), and subqueries. The room also introduces database normalization and relationships (one-to-one, one-to-many, many-to-many). Security focus includes understanding how unsanitized input can lead to SQL injection attacks, setting the stage for web exploitation techniques.

## Room 4: Burp Suite: The Basics

- **URL**: https://tryhackme.com/room/burpsuitebasics
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

This room introduces Burp Suite, the most widely used web application security testing platform. Learners configure their browser to route traffic through Burp Suite's proxy, intercept HTTP requests and responses, and modify them in real-time. The room covers the Repeater tool for resending and modifying individual requests, the Intruder tool for automated parameter fuzzing, and the Decoder for encoding and decoding data. Practical exercises involve intercepting login forms, manipulating request parameters, and observing how server-side validation can be bypassed.

## Room 5: OWASP Top 10 - 2021

- **URL**: https://tryhackme.com/room/owasptop102021
- **Difficulty**: Easy
- **Subscription**: Free
- **Estimated Time**: ~2 hours

The OWASP Top 10 - 2021 room provides a comprehensive overview of the most critical web application security risks. Each of the ten categories is explained with real-world examples, exploitation techniques, and mitigation strategies. The room covers Broken Access Control (allowing users to act outside their permissions), Cryptographic Failures (exposed sensitive data), Injection (SQL, NoSQL, OS command), Insecure Design (architecture-level flaws), Security Misconfiguration (default credentials, unnecessary features), Vulnerable and Outdated Components (unpatched libraries), Identification and Authentication Failures (weak password policies), Software and Data Integrity Failures (untrusted updates), Security Logging and Monitoring Failures (insufficient incident detection), and Server-Side Request Forgery (SSRF). This room ties together all the concepts from earlier rooms and provides a holistic view of web application security.
