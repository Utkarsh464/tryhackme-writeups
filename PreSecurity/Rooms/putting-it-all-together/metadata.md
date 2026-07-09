# Putting It All Together

## Room Information
- **Room URL:** https://tryhackme.com/room/putting-it-all-together
- **Module:** How The Web Works
- **Difficulty:** Very Easy
- **Estimated Time:** 20-30 min
- **Access:** Free

## Description
This room is the capstone of the How The Web Works module, bringing together DNS, HTTP, and web technologies into a single cohesive narrative. Students trace the complete lifecycle of a web request: from typing a URL in the browser, through DNS resolution, TCP and TLS handshakes, HTTP request/response, server processing, and finally browser rendering.

Understanding the full request lifecycle gives students a holistic view of web security. Every step — DNS resolution (spoofing), TCP handshake (SYN flood), TLS negotiation (certificate validation), HTTP request (header injection), server processing (SQL injection), and browser rendering (XSS) — is a potential attack surface.

## Learning Objectives
- Trace the full lifecycle of a web request from URL entry to page render
- Explain DNS resolution, TCP handshake, and TLS handshake
- Describe how the browser renders HTML, CSS, and JavaScript
- Identify security considerations at each stage of the lifecycle

## Key Tools and Technologies
- Browser DevTools
- curl
- Wireshark
- dig

## Prerequisites
- DNS in Detail
- HTTP in Detail
- How Websites Work

## Expected Outcomes
Students will be able to describe every step that occurs when a user visits a website, from DNS resolution through to the final rendered page, and identify security implications at each stage.
