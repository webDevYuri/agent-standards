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
- `agent-guides/code-style.md` — Readability and scoped formatting rules
- `agent-guides/payments.md` — New payment integration safety checklist
- `agent-guides/access.md` — Project-local access opt-ins

## Usage

Copy the files into the root of your project while preserving the existing folder structure.

Your coding agent should read `AGENTS.md` first. It will route the agent to the relevant guide and sections based on the current task.

### Task-Based Loading

Read global rules in full, then only the routed guides and sections. Follow their required references, expand coverage when scope or risk grows, and reuse instructions already in context. Safety, permission, and verification requirements still apply; savings come from avoiding unrelated reading rather than omitting relevant rules.

| Task | Relevant guidance |
|------|-------------------|
| Small styling fix | Engineering core, code style, affected frontend sections, UI/UX baseline and affected visual sections |
| New dashboard | Engineering core, code style, affected frontend sections, UI/UX screen design and data guidance |
| Form redesign | Engineering core, code style, affected frontend sections, UI/UX baseline, forms, states, responsiveness, and accessibility |
| Backend-only change | Engineering core, code style, affected backend sections; local API verification when behavior changes |

These examples are starting points; follow routing for additional concerns such as contracts, security, or payments. Compare required reading by word count when assessing efficiency; exact token usage depends on the agent, tokenizer, and task.

### UI/UX Workflow

For new screens and meaningful redesigns: understand the user task, choose a coherent design direction, build with existing components and tokens, then review the affected flow locally. Small fixes need only relevant checks. Adapt to each product and brand rather than imposing one visual style.

Visual changes must preserve existing functionality, essential actions, validation, API contracts, and permissions. Identify behavior changes separately before implementation. Report what was verified and any remaining limitations; guidelines cannot guarantee that an untested interface works.

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
