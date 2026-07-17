# Agent Standards

A practical, token-efficient rulebook for AI coding agents.

This repository contains reusable standards for:

- General engineering principles
- Backend development
- Frontend development
- UI/UX design
- Context-first codebase investigation
- URL-based route discovery
- Local API endpoint verification

The goal is to help coding agents produce safer, simpler, more maintainable, and less generic output without replacing the built-in capabilities of tools such as Codex, Cursor, Claude Code, or Gemini CLI.

## Included Files

- `AGENTS.md` — Global rules and instruction routing
- `agent-guides/engineering.md` — Universal engineering principles and investigation rules
- `agent-guides/backend.md` — Backend-specific development standards
- `agent-guides/frontend.md` — Frontend-specific development standards
- `agent-guides/uiux-ds.md` — UI/UX design standards and AI-slop prevention
- `agent-guides/testing.md` — Local API endpoint verification rules

## Usage

Copy the files into the root of your project while preserving the existing folder structure.

Your coding agent should read `AGENTS.md` first. It will route the agent to the relevant guide and sections based on the current task.

## Project-Specific Notes

Before using these standards, open `AGENTS.md` and find:

```md
## Project-Specific Notes
```

Replace the contents of that section with information specific to your project.

This may include:

- Tech stack
- Project structure
- Coding conventions
- Development commands
- Local environment setup
- Installed UI component libraries
- Important architectural decisions
- Testing commands
- Database restrictions
- External service restrictions
- Project-specific safety rules

Do not keep the default notes when they do not accurately describe your project.

## Important

These files provide behavioral guidance for coding agents. They do not install packages, create custom codebase indexes, or replace the search, indexing, and execution capabilities already provided by your coding tool.
