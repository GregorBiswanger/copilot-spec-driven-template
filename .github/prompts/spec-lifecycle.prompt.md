---
name: spec-lifecycle
description: Manage spec status and move specs between backlog/active/done.
argument-hint: "spec=<path or #file> newStatus=<Draft|In Progress|Implemented|Deprecated> (optional)"
agent: SpecDrivenAgent
---

# /spec-lifecycle — Manage Spec Status and Folders

> **Usage:** `/spec-lifecycle spec=<path or #file> newStatus=<...>`
> (You can also just answer questions if the prompt asks.)


When invoked, you help manage the lifecycle of specs under `.github/specs/`.

## Goal

Keep the spec set tidy by:
- Updating spec status fields.
- Moving specs between `backlog/`, `active/`, and `done/`.
- Keeping the Memory Bank aligned with important spec changes.

## Rules

- Spec files are Markdown and must be written in the language specified by `DocLanguage` in `.github/copilot-instructions.md` (default English until set).
- Specs are organized by lifecycle stage:
  - `.github/specs/backlog/` — ideas and not-yet-started specs.
  - `.github/specs/active/` — specs currently being implemented.
  - `.github/specs/done/` — implemented specs with passing acceptance criteria.
- Each spec should declare a status near the top, for example:
  - `**Status:** Draft | In Progress | Implemented | Deprecated`
- Only move a spec to `done/` when its acceptance criteria are satisfied and relevant tests pass.

## Default behavior

When I run `/spec-lifecycle` and reference one or more specs, you should:

1. **Inspect** the referenced spec(s):
   - Read title, summary, acceptance criteria, and any existing status field.
2. **Propose** a lifecycle update, for example:
   - Move draft ideas into `backlog/`.
   - Move currently implemented work into or within `active/`.
   - Move completed specs into `done/` and set status to `Implemented`.
3. **Act** on the agreed update:
   - Edit the spec file to adjust the `Status` line.
   - Move the spec into `backlog/`, `active/`, or `done/` as appropriate.
4. **Sync documentation**:
   - If the spec introduces or changes architecture, tests, or tooling, update the relevant Memory Bank files in `.github/memory-bank/`.

## Do / Don't

**Do**
- Keep changes minimal and focused on spec lifecycle.
- Preserve existing spec structure, wording, and links.
- Use clear, concise language when editing specs (follow `DocLanguage`).
- Mention in your summary which specs moved and how their status changed.

**Don't**
- Change the technical content of a spec unless explicitly requested.
- Create or remove specs without the user asking for it.
- Modify code outside of spec and Memory Bank files unless the user asks.