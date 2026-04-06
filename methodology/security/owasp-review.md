---
title: OWASP Review
description: Review all code for OWASP top 10 vulnerabilities. Injection, broken auth, data exposure, XSS, and more.
cluster: security
related: [[secrets-management]], [[../verification/validate-before-claiming]]
source: OWASP Foundation -- industry standard for web application security
---

# OWASP Review

Every code change that touches user input, authentication, data storage, or API endpoints gets reviewed against the OWASP top 10.

## The Top 10 (2021, still current)

1. **Broken Access Control** -- users accessing things they shouldn't
2. **Cryptographic Failures** -- weak encryption, plaintext storage
3. **Injection** -- SQL injection, command injection, XSS
4. **Insecure Design** -- missing security controls in the architecture
5. **Security Misconfiguration** -- default credentials, verbose errors, open cloud storage
6. **Vulnerable Components** -- outdated dependencies with known CVEs
7. **Authentication Failures** -- weak passwords, missing MFA, session issues
8. **Data Integrity Failures** -- trusting unsigned data, insecure deserialization
9. **Logging Failures** -- not logging security events, logging sensitive data
10. **SSRF** -- server making requests to unintended destinations

## Quick Check for Every PR

- [ ] User input validated and sanitized?
- [ ] SQL queries parameterized (no string concatenation)?
- [ ] Auth checks on every endpoint that needs them?
- [ ] No secrets in code, logs, or error messages?
- [ ] Dependencies up to date?
- [ ] Error messages don't leak implementation details?
