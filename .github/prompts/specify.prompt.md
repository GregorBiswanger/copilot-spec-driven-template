---
name: specify
description: Create or refine a spec (acceptance criteria first).
argument-hint: "title=<short> area=<folder/module>"
agent: SpecDrivenAgent
---

# /specify — Create a Spec 

> **Usage:** `/specify title=<short> area=<folder/module>`
> (You can also just answer questions if the prompt asks.)


## Instructions
- Ask for: goal, scope, non-goals, constraints, acceptance criteria, risks.
- Propose a spec filename under `.github/specs/` and write it.

## Output format
Create a Markdown file with:
- Summary
- Problem / Motivation
- Goals / Non-goals
- Requirements
- Acceptance Criteria (testable)
- Open Questions
- Out of Scope