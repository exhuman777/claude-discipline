---
name: discipline-review
description: Methodology-backed code review that checks code against discipline rules across security, verification, planning adherence, entropy, and efficiency. Goes beyond style checks.
license: MIT
metadata:
  author: exhuman
  version: "1.0"
  plugin: claude-discipline
---

# Discipline Code Review

Review code against the claude-discipline methodology.

## Review Dimensions

### 1. Security
- [ ] User input validated and sanitized?
- [ ] No SQL injection, XSS, or command injection vectors?
- [ ] No secrets in code or logs?
- [ ] Auth checks on protected endpoints?
- [ ] Dependencies up to date?

### 2. Verification
- [ ] Tests exist for new/changed behavior?
- [ ] Tests are real (test actual behavior, not just existence)?
- [ ] Tests cover edge cases, not just happy path?
- [ ] All claims in comments/docs match actual behavior?

### 3. Planning Adherence
- [ ] Implementation matches the plan/spec?
- [ ] No A' approximations (simpler but different from spec)?
- [ ] Complexity decomposed into manageable pieces?
- [ ] Solution scales (founder mindset, not contractor)?

### 4. Entropy Check
- [ ] All references to changed things updated?
- [ ] Comments accurate?
- [ ] Docs reflect current behavior?
- [ ] No stale TODO/FIXME comments?

### 5. Efficiency
- [ ] No unnecessary complexity?
- [ ] DRY -- no duplicated logic?
- [ ] YAGNI -- no speculative features?

## Output Format

For each dimension, state PASS or FAIL with specifics:
```
Security: PASS
Verification: FAIL -- no test for error handling in submitForm()
Planning: PASS
Entropy: FAIL -- README still references old API endpoint
Efficiency: PASS
```

See the [claude-discipline methodology](https://github.com/exhuman777/claude-discipline) for the full skill graph.
