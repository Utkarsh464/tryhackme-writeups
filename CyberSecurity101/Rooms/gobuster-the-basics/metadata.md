# Gobuster: The Basics

## Room Information
- **URL**: https://tryhackme.com/room/gobusterthebasics
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

## Description

Gobuster is a high-performance tool for brute-forcing directories, DNS subdomains, and virtual hosts on web servers. Written in Go, Gobuster offers significant speed advantages over traditional tools like dirb or dirbuster because Go's concurrent execution model handles multiple HTTP requests efficiently. This room introduces the three primary modes of operation: directory/file enumeration (dir mode), DNS subdomain enumeration (dns mode), and virtual host enumeration (vhost mode). In directory enumeration mode, Gobuster takes a base URL and a wordlist, then sends HTTP requests for each word as a path segment, analyzing response status codes to identify existing resources. Status codes 200 (OK), 301/302 (redirect), and 403 (forbidden) typically indicate discovered resources, while 404 (not found) indicates non-existent paths. The room covers how to interpret status codes to distinguish between accessible resources and false positives. In DNS mode, Gobuster queries DNS servers with each word from a wordlist prepended to a target domain, and identifies which subdomains resolve to IP addresses. This is a critical reconnaissance technique for expanding the attack surface during penetration tests. In vhost mode, Gobuster sends HTTP requests with different Host headers to identify virtual hosts hosted on the same web server. The room also covers practical aspects including wordlist selection and organization, managing request rate and concurrency with the -t flag, handling various HTTP response codes with the -s flag, and configuring HTTP options like cookies, user agents, and authentication for targeted scanning.

## Objectives
- Install and configure Gobuster for directory, DNS, and vhost enumeration
- Discover hidden directories and files on web servers
- Enumerate DNS subdomains for a given domain
- Identify virtual hosts hosted on shared web servers
- Interpret HTTP status codes to evaluate findings
- Optimize scan performance with appropriate flags

## Tools
- Gobuster
- SecLists wordlist collection
- DNS resolution tools (dig, nslookup)

## Concepts
- Directory and file brute-forcing
- DNS subdomain enumeration
- Virtual host discovery
- HTTP status code interpretation
- Concurrent scanning and rate limiting
- Web reconnaissance methodology
