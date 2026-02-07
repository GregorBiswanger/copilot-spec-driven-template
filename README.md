# Spec-Driven Development Template for GitHub Copilot

This template provides a **Spec-Driven Development (SDD)** setup that lives entirely under `/.github`.

## How to start
1. In VS Code Copilot Chat, select the **SpecDrivenAgent**.
2. Run **/setupSpecs** to choose your documentation language and bootstrap the Memory Bank + spec folders.

## Key folders
- `.github/memory-bank/` — project context (brief, patterns, active context, tech context)
- `.github/specs/` — specs by lifecycle (`backlog/`, `active/`, `done/`)
- `.github/prompts/` — reusable workflows (run via `/...`)
- `.github/agents/` — custom agent configuration
- `.github/copilot-instructions.md` — repository-wide rules (architecture snapshot + style preferences)

## Recommended workflow
- `/specify` → `/plan` → implement → `/compile` → `/spec-lifecycle`
- Use `/architecture-update` whenever structure changes (the agent also attempts best-effort automatic sync).
