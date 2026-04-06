---
name: review
description: Methodology-backed code review. Checks code against discipline rules, not just style. Crosses verification + security + planning clusters.
---

# Discipline Code Review

Review code against the claude-discipline methodology.

## Review Dimensions

### 1. Security (from security cluster)
- [ ] User input validated and sanitized?
- [ ] No SQL injection, XSS, or command injection vectors?
- [ ] No secrets in code or logs?
- [ ] Auth checks on protected endpoints?
- [ ] Dependencies up to date?

### 2. Verification (from verification cluster)
- [ ] Tests exist for new/changed behavior?
- [ ] Tests are real (test actual behavior, not just existence)?
- [ ] Tests cover edge cases, not just happy path?
- [ ] All claims in comments/docs match actual behavior?

### 3. Planning Adherence (from planning cluster)
- [ ] Implementation matches the plan/spec?
- [ ] No A' approximations (simpler but different from spec)?
- [ ] Complexity decomposed into manageable pieces?
- [ ] Solution scales (founder mindset, not contractor)?

### 4. Entropy Check (from agent-discipline cluster)
- [ ] All references to changed things updated?
- [ ] Comments accurate?
- [ ] Docs reflect current behavior?
- [ ] No stale TODO/FIXME comments?

### 5. Efficiency (from token-efficiency cluster)
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

## Methodology Reference

This skill crosses multiple clusters. See `methodology/index.md` for the full graph.
