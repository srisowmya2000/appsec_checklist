# Web Application Security Checklist

A simple and practical GitHub repository for learning and reviewing web application security.

This project helps developers, security engineers, AppSec learners, and bug bounty hunters understand:

- common web application vulnerabilities
- how they appear in real applications
- how they differ across programming languages and frameworks
- how to test for them
- how to fix or mitigate them

---

## Why this project?

Web applications are built with different stacks, but many security issues repeat across them.This repository aims to make web application security easier to understand by showing:

- what the vulnerability is
- where it commonly appears
- how it looks in different code languages
- what the impact is
- how to mitigate it

This is designed to be:

- beginner-friendly
- practical
- simple to maintain
- easy to expand over time

---

## Who is this for?

- Developers
- Security Engineers
- Application Security learners
- Bug Bounty Hunters
- Students learning web security
- Anyone doing secure code review or manual testing

---

## What this repository covers

This project focuses on common web application security areas such as:

- Authentication
- Session Management
- Access Control
- Input Validation
- Output Encoding
- File Upload Security
- API Security
- Security Misconfiguration
- Dependency Risks
- Common OWASP-style web vulnerabilities

---

## Repository Structure

```bash
webapp-security-checklist/
│
├── README.md
├── checklist/
│   ├── web-app-checklist.md
│   ├── auth-checklist.md
│   └── api-checklist.md
│
├── vulnerabilities/
│   ├── xss.md
│   ├── sqli.md
│   ├── csrf.md
│   ├── idor.md
│   ├── ssrf.md
│   ├── file-upload.md
│   ├── security-misconfig.md
│   └── auth-bypass.md
│
├── stacks/
│   ├── php.md
│   ├── python.md
│   ├── nodejs.md
│   ├── java.md
│   └── dotnet.md
│
└── examples/
    ├── vulnerable-code-examples.md
    └── secure-code-examples.md
