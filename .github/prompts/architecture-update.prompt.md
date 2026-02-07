---
name: architecture-update
description: Detect architecture drift and sync snapshot + Memory Bank.
argument-hint: "Focus=<module|folder|area> (optional)"
agent: SpecDrivenAgent
---

# /architecture-update — Architecture Reconciliation

> **Usage:** `/architecture-update Focus=<module|folder|area>`
> (You can also just answer questions if the prompt asks.)


## Goal
Compare:
- The actual repository directory structure (use `@workspace` / `#codebase`)
vs.
- The `architecture:` snapshot in `.github/copilot-instructions.md`

## Steps
1. Load the current `architecture:` YAML from `.github/copilot-instructions.md`.
2. Scan the repository structure. Identify changes that matter architecturally:
   - new/moved/removed top-level folders
   - new entrypoints, apps, services, packages, modules
   - changed boundaries or shared components
3. Present a **delta report** to the user:
   - What changed (observed)
   - Why it matters (brief)
   - Proposed updates to the snapshot and Memory Bank docs

## Confirmation gate
Ask the user:
- "Is this the change you expected?"
- "Anything else I should include (e.g., you added context that isn't visible in code)?"

Only after confirmation:
- Update `.github/copilot-instructions.md` architecture YAML
- Update `.github/memory-bank/systemPatterns.md` (patterns/decisions)
- Update `.github/memory-bank/activeContext.md` (recent changes + next steps)

Everything must remain **DocLanguage-aware**.