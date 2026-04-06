# 7 Agent Failure Modes -- Quick Reference

| # | Mode | Signs | Fix |
|---|------|-------|-----|
| 1 | **Incomplete Context** | Coding without reading all files | Read ALL related files first |
| 2 | **Misalignment** | Quick fix instead of right fix | Think founder, not contractor |
| 3 | **Context Anxiety** | Quality drops late in session | /compact or hand off summary |
| 4 | **Planning Deviations** | A' instead of A | Verify against plan each step |
| 5 | **Complexity Fear** | Stubs, "out of scope" | Decompose to sub-100-line tasks |
| 6 | **Verification Laziness** | "Should work", no evidence | Run checks, show output |
| 7 | **Entropy Maximization** | Stale docs after changes | Update ALL references |

## Detection Shortcuts

**Hearing "it should work"?** -> Failure mode 6. Ask for evidence.

**Seeing TODO/stub in output?** -> Failure mode 5. Decompose the hard part.

**Quality dropping?** -> Failure mode 3. Compact or fresh session.

**Implementation doesn't match plan?** -> Failure mode 4. Re-read plan, fix deviation.

**Agent started coding immediately?** -> Failure mode 1. Run /discipline:audit.

## Key Insight

Agent psychology = human psychology. Same fixes: break tasks small, verify often, clean as you go.
