<!-- Public overview, setup instructions, and supported-agent guidance. -->

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

## Supported Agents

You may need to rename the primary instruction file depending on the coding agent you use.

| Agent | Instruction File |
|-------|------------------|
| Codex | `AGENTS.md` |
| Cursor | `AGENTS.md` |
| Claude Code | `CLAUDE.md` |
| Gemini CLI | `GEMINI.md` |

Check your coding agent's documentation if it requires a different instruction filename.

## Important

These files provide behavioral guidance for coding agents. They do not install packages, create custom codebase indexes, or replace the search, indexing, and execution capabilities already provided by your coding tool.
