---
name: style-update
description: Capture or reorganize coding style preferences in copilot-instructions.
argument-hint: "Add=<preference> (or list multiple)"
agent: SpecDrivenAgent
---

# /style-update — Capture Coding Style Preferences

> **Usage:** `/style-update Add=<preference> (repeatable)`
> (You can also just answer questions if the prompt asks.)


## Goal
Update **Style & Output Preferences** in `.github/copilot-instructions.md`.

## Steps
1. Ask the user for the preference(s) if not provided.
2. Normalize them into short bullets grouped by category (Comments, Naming, Formatting, Framework Conventions, Testing, etc.).
3. Apply updates immediately to `.github/copilot-instructions.md`.
4. Confirm by showing the updated bullets.