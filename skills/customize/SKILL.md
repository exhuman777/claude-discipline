---
name: customize
description: Interactive CLAUDE.md generator that walks through questions about your workflow, domain, team size, and communication style, then generates a customized ruleset from 3 template tiers.
license: MIT
metadata:
  author: exhuman
  version: "1.0"
  plugin: claude-discipline
---

# CLAUDE.md Customizer

Generate a customized CLAUDE.md based on your workflow and preferences.

## Process

Ask the user these questions one at a time. Based on answers, select the appropriate template tier and toggle rule categories.

### Question 1: Scope
"What level of discipline do you want?"
- **Minimal (10 rules)** -- essentials only: security, verification, planning basics
- **Standard (25 rules)** -- recommended: adds token efficiency, all failure mode guards, context management
- **Maximal (43 rules)** -- everything: includes customizable sections for aesthetics, routing, identity

### Question 2: Domain
"What kind of work do you primarily do with Claude Code?"
- **Web development** -- adds: OWASP focus, deployment rules, port checking
- **Backend/API** -- adds: API security, database safety, secrets management emphasis
- **Data/ML** -- adds: notebook discipline, experiment tracking
- **General/mixed** -- balanced ruleset

### Question 3: Team
"Solo developer or team?"
- **Solo** -- simpler git rules, no PR process
- **Team** -- adds: PR protocol, branch naming, commit message conventions

### Question 4: Style
"Communication preference?"
- **Terse** -- maximum brevity, caveman output, no filler
- **Balanced** -- brief but explains decisions when useful
- **Detailed** -- fuller explanations, good for learning

### Question 5: Customization
"Any personal preferences to include?"
- Open-ended: aesthetic preferences, port reservations, project routing, gotchas
- These go into a "Personal" section at the end of the CLAUDE.md

## Generation

Based on answers:
1. Select the base template (minimal, standard, or maximal)
2. Toggle domain-specific rules on/off
3. Adjust team/solo settings
4. Set communication style
5. Append personal preferences section
6. Write to ~/CLAUDE.md

## Output

"Generated your CLAUDE.md at ~/CLAUDE.md with [N] rules. Here's a summary of what's included: [category list]"

## Templates

Three tiers available:
- **minimal.CLAUDE.md** (10 rules) -- security, verification, planning basics
- **standard.CLAUDE.md** (25 rules) -- adds token efficiency, failure mode guards
- **maximal.CLAUDE.md** (43 rules) -- full ruleset with customizable sections

See the [claude-discipline methodology](https://github.com/exhuman777/claude-discipline) for the full skill graph.
