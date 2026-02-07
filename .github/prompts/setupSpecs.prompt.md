---
name: setupSpecs
description: Bootstrap Spec-Driven Development docs, Memory Bank, and spec folders under .github/.
argument-hint: 'docLanguage=<English|German|...> projectName=<name> stack=<tech> (or just answer the wizard)'
agent: SpecDrivenAgent
---

# /setupSpecs — SDD Setup Wizard

> **Usage:** `/setupSpecs docLanguage=<English|German|...> projectName=<name> stack=<tech>`
> (You can also just answer questions if the prompt asks.)

You are running an onboarding wizard for a new repository.

## Spec-Driven Development (SDD) – Orientation for the model

On the very first invocation of this prompt, start with a short introduction to Spec-Driven Development and to the available SDD prompts in this repository. Right after that, immediately ask **Step 0** (the language question).

For the central definition of SDD, use the following text verbatim (unchanged, in English), and optionally surround it with a brief English explanation if helpful:

**Spec-Driven Development (SDD)** is an AI-assisted development approach where a **clear, structured, versioned specification** is the **primary artifact**. Implementation, tests (and often documentation) are **derived from the spec** and then **continuously validated against it** in an iterative loop (**generate → verify/validate → refine**).

For quality with coding assistants: because assistants/agents generate code **anchored to an explicit spec**—and outputs can be **checked, corrected, and regenerated** based on that spec—SDD helps **ensure higher-quality, more maintainable code** than unstructured prompt- or “vibe”-driven coding.

Key principles:

- **Spec-first:** define _what_ to build (behavior, acceptance criteria, constraints) before writing code.
- **Structured specification:** not just loose user stories—structured enough for consistent tool/agent execution.
- **Living spec:** the spec evolves with the system and remains the reference point for change.
- **Spec-as-source:** the spec is the enduring source of truth; code is (re)generatable from it.

Therefore, at the beginning, explain to the user in 2–4 English sentences that:

- SDD means specifications are the primary reference point and code/tests are derived from them.
- collaboration with GitHub Copilot here always follows the cycle "specify → plan → implement → validate against the specification".
- the prompts in this repository are designed to guide you through exactly this SDD workflow.

## Overview: When to use which prompt?

After the short SDD introduction, give the user a concise orientation (in English) about which SDD prompts exist in this repository and what they are good for. Use this mapping:

- `/setupSpecs`: One-time (or occasional) onboarding of a repository for SDD – sets DocLanguage, prepares Memory Bank and specs folders under `.github/`, and initializes the first architecture snapshot.
- `/specify`: When you want to concretize a new feature/idea – creates or refines a specification with clear acceptance criteria under `.github/specs/`.
- `/plan`: When you need an actionable implementation plan for an existing specification – reads a selected spec and produces a step-by-step plan with checkpoints.
- `/architecture-update`: When the repository structure has changed or you suspect architecture drift – compares the current codebase to the architecture snapshot and updates it plus the Memory Bank (after confirmation).
- `/spec-lifecycle`: When you want to maintain the status of specifications or move specs between `backlog/`, `active/`, and `done/`.
- `/style-update`: When new coding-style preferences should be captured or existing ones refined – updates the "Style & Output Preferences" section in `.github/copilot-instructions.md`.

Keep this overview short and orienting; avoid deep implementation details.

After this, transition directly into the onboarding dialog, starting with Step 0.

## Step 0 (MUST be the first question)

Ask exactly this question first:

**"In which language should the project documentation Markdown files be written?"**

### Constraint

- If the user does not answer the language question, infer it from the current conversation language.
- After a language is chosen, set `DocLanguage` in `.github/copilot-instructions.md`.
- Then ensure all project docs (Memory Bank + specs) are written in that language (rewrite the default English templates if needed).

## Wizard steps (ask in order; keep it friendly & minimal)

1. **Project name & one-liner**
2. **Primary users / target audience**
3. **Tech stack** (languages, frameworks, runtime, package managers)
4. **Architecture style** (modular monolith / microservices / layered / hexagonal / other)
5. **Repo entrypoints** (apps, services, CLIs, APIs)
6. **Quality gates** (tests, lint/format, CI)
7. **Coding preferences** (e.g., comments, naming, patterns to avoid)

## Actions you must perform

After collecting the answers:

A) **Scaffold / ensure folders** (under `.github/` only):

- `.github/memory-bank/`
- `.github/specs/backlog/`, `.github/specs/active/`, `.github/specs/done/`
- keep `.github/prompts/`, `.github/agents/`, `.github/instructions/`

B) **Initialize documentation** in `DocLanguage`:

- Update `.github/memory-bank/projectbrief.md` with project mission + success criteria
- Update `.github/memory-bank/techContext.md` with stack + build/run/test
- Create an initial `.github/memory-bank/activeContext.md` (current focus + next steps)
- Create/update `.github/memory-bank/systemPatterns.md` (initial patterns/decisions)

C) **Initial architecture capture (best-effort automatic)**

- Inspect the current workspace structure (`@workspace` / `#codebase`).
- Populate the `architecture:` snapshot in `.github/copilot-instructions.md` based on the folder/project layout.
- If assumptions are required, write them down and ask the user to confirm them (one concise question).

D) **Style preference capture**

- Seed “Style & Output Preferences” in `.github/copilot-instructions.md` with what the user stated.

## Output

- Summarize what you created/updated and what you inferred.
- Provide 1–3 suggested next commands: `/specify`, `/plan`, `/architecture-update`, `/spec-lifecycle`.
