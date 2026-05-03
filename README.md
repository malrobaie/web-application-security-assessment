# Web Application Security Assessment

## Overview

This project documents a structured application security assessment of a locally hosted vulnerable web application using OWASP Top 10 methodology, manual testing, and dynamic application security testing tools.

The goal of this project is to simulate the work of an Application Security Engineer by identifying vulnerabilities, documenting technical evidence, assessing business impact, and recommending secure remediation strategies.


Key skills demonstrated:
- Manual security testing (Burp Suite)
- API and access control analysis
- XSS and injection testing
- Secure data handling analysis
- Vulnerability reporting and remediation

## Target Application

**Application:** OWASP Juice Shop  
**Environment:** Local Docker container  
**URL:** `http://localhost:3000`  
**Purpose:** Intentionally vulnerable web application used for legal security training and assessment.

## Scope

The assessment focused on:

- Authentication and login flows
- Input validation
- API request and response behavior
- Access control weaknesses
- Client-side storage and sensitive data exposure
- Common OWASP Top 10 risks
- AI/LLM security considerations for modern applications

## Tools Used

- Docker
- Burp Suite Community Edition
- OWASP ZAP
- Browser Developer Tools
- Manual testing methodology
- OWASP Top 10 framework

## Assessment Methodology

1. Deployed OWASP Juice Shop locally using Docker.
2. Explored application functionality and user workflows.
3. Used Burp Suite to intercept and analyze HTTP requests.
4. Used OWASP ZAP to perform automated DAST scanning, identifying multiple medium and low severity vulnerabilities and validating manual findings.
5. Manually tested for common vulnerabilities such as SQL Injection, XSS, broken access control, and sensitive data exposure.
6. Documented findings with severity, evidence, impact, and remediation guidance.
7. Added AI/LLM security considerations based on modern application risk patterns.

## Key Findings

| Finding | Severity | OWASP Category | Status |
|---|---:|---|---|
| SQL Injection | High | Injection | Documented |
| Cross-Site Scripting | Medium | Injection / XSS | Documented |
| Broken Access Control | High | Broken Access Control | Documented |
| Sensitive Data Exposure | Medium | Cryptographic Failures / Security Misconfiguration | Documented |

## Repository Structure

```text
web-application-security-assessment/
├── README.md
├── report/
│   └── vulnerability-assessment-report.md
├── screenshots/
│   ├── 01-juice-shop-running.png
│   ├── 02-burp-proxy-configured.png
│   ├── 03-login-request-intercepted.png
│   ├── 04-sql-injection-result.png
│   ├── 05-xss-payload-result.png
│   ├── 06-access-control-original.png
│   ├── 06-access-control-modified.png
│   ├── 06-access-control-invalid.png
│   ├── 07-local-storage.png
│   ├── 07-session-storage.png
│   ├── 07-cookies.png
│   └── 08-zap-scan-results.png
└── notes/
    └── testing-notes.md

```

## Disclaimer

This assessment was performed only against a locally hosted intentionally vulnerable application. No unauthorized systems, networks, or third-party applications were tested.
