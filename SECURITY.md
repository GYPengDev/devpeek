# Security Policy

## Supported versions

Security fixes are delivered through DevPeek desktop releases. Install the latest stable build from:

- https://devpeek.ypgao.com/
- https://github.com/GYPengDev/devpeek/releases

## Reporting a vulnerability

**Please do not open a public GitHub issue for security vulnerabilities.**

Instead, report privately via:

- https://devpeek.ypgao.com/en/contact/ (subject: Security)
- Or the contact channel listed on the website

Include:

- DevPeek version and OS (Windows / macOS, including architecture)
- Steps to reproduce
- Impact assessment (data exposure, MITM scope, local privilege, etc.)

We aim to acknowledge reports within **5 business days** and will coordinate disclosure after a fix or mitigation is available.

## Scope notes

DevPeek performs **local HTTPS interception** using a user-installed root CA. This is intentional product behavior for authorized debugging on devices you control. Misconfiguration or sharing the CA with untrusted parties increases risk — follow the [proxy & SSL docs](https://devpeek.ypgao.com/en/docs/proxy-ssl/) and only intercept traffic you are permitted to inspect.

## Out of scope

- Issues caused by debugging third-party apps without authorization
- Social engineering or physical access to an unlocked machine
- Vulnerabilities in upstream dependencies already fixed in the latest release (still report — we will verify and backport if needed)
