# Security Policy

## Supported Versions

| Version | Supported |
| ------- | --------- |
| latest  | Yes       |

## Reporting a Vulnerability

If you discover a security vulnerability, please report it responsibly:

1. **Do NOT** open a public issue
2. Email: knowledgeknight99@protonmail.com
3. Include a description and steps to reproduce
4. Allow 48 hours for initial response

## Scope

This repository contains CI/CD workflow templates. Security concerns include:
- Workflow injection vulnerabilities
- Secret exposure in workflow logs
- Unsafe use of `pull_request_target`
- Unvalidated external action versions
