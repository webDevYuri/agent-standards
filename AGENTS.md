<!--
This is the primary instruction file that coding agents should read first.
It defines the global safety and working rules that apply to every task,
then routes the agent to only the task-specific guides and sections it needs.
-->

# AGENTS.md

## Purpose

These rules apply to every task. Prioritize correctness, security, permissions, maintainability, and preservation of user work.

## Instruction Routing

Read this file for every task. Classify the request and affected paths, then load only the linked sections that apply. Token efficiency never overrides correctness, security, permissions, production or data safety, or preservation of user work.

* **Implementation, maintenance, or refactoring:** Read engineering [Core Principles](agent-guides/engineering.md#core-principles).
* **User-provided files, snippets, or exact paths:** Start there. Load [Context-First Investigation](agent-guides/engineering.md#context-first-investigation) only if that context is insufficient.
* **Unknown files or insufficient context:** Read [Context-First Investigation](agent-guides/engineering.md#context-first-investigation).
* **Application URL supplied instead of files:** Read [URL-Driven Route Discovery](agent-guides/engineering.md#url-driven-route-discovery); add investigation guidance only if targeted route discovery fails.
* **Debugging:** Read engineering [Core Principles](agent-guides/engineering.md#core-principles) and [Debugging and Verification](agent-guides/engineering.md#debugging-and-verification); add investigation guidance only when needed.
* **Backend:** Use backend [Section Routing](agent-guides/backend.md#section-routing) for APIs, authentication, authorization, validation, databases, transactions, migrations, queues, jobs, integrations, or server configuration. Load only matched headings.
* **Frontend:** Use frontend [Section Routing](agent-guides/frontend.md#section-routing) for components, state, data fetching, rendering, browser behavior, or framework code. Load only matched headings.
* **Visual or UX:** Use frontend [Section Routing](agent-guides/frontend.md#section-routing) and UI/UX [Section Routing](agent-guides/uiux-ds.md#section-routing) for layout, styling, usability, responsive behavior, presentation, interaction states, forms, tables, navigation, typography, accessibility, or animation. Do not load UI/UX guidance for non-visual frontend work.
* **API verification:** Use testing [Section Routing](agent-guides/testing.md#section-routing) for new endpoints, endpoint bugs, endpoint runtime, authentication, authorization, validation, database writes, statuses, response shapes, or explicit endpoint verification. Do not load it for unrelated backend work or strictly non-behavioral endpoint changes.

If scope expands, load only newly relevant sections before continuing. Do not reopen unchanged instructions still available in context. For mixed, uncertain, security-sensitive, broad-audit, or architectural work, load the broader relevant sections or complete guides only when scope cannot be narrowed safely. Higher-priority and stricter rules win; ask when the safe interpretation is unclear.

## Scope and User Work Protection

* Modify only requested files and necessary dependencies. Avoid unrelated refactors and whole-file reformatting.
* Inspect files before substantial edits. Preserve unrelated code, formatting, and user changes.
* Never discard unexpected or overlapping work; ask how to proceed.
* Do not run formatters or linters in rewrite mode unless formatting is intended.

## Environment and Secrets

* Never read, print, inspect, or modify `.env` files; use only example files such as `.env.example`, `.env.local.example`, or `.env.testing.example`.
* Never expose, guess, fabricate, or hardcode secrets, keys, tokens, passwords, credentials, or private URLs.
* Use environment variables only for secrets or values that genuinely vary by environment. Keep stable, non-sensitive configuration in version control; avoid duplicate or speculative variables.
* Document a necessary variable only by name and safe placeholder in the appropriate example file. Infer names from examples or code; if blocked, ask instead of inspecting secret files.
* Never log sensitive values, payment data, or personal information.

## Production and External Systems

* Never SSH into or directly access live, staging, or production infrastructure, or run commands against its servers, databases, queues, storage, or third-party production services.
* Debug and verify locally. Use another safe environment only with explicit authorization and when every other rule permits it.
* API endpoint verification is always local-only under [Local Environment Only](agent-guides/testing.md#local-environment-only--non-negotiable); authorization cannot override this restriction.
* For production issues, explain safe checks for the user to run.

## Side Effects and External Actions

* Do not send real email, SMS, push, payment, webhook, or other external actions without explicit approval.
* Use local fakes, mocks, logs, test or sandbox mode, or dry runs. Confirm safe configuration before code can contact an external service.
* Never trigger effects on real users, customers, orders, payments, inventory, subscriptions, or notifications.

## Dependencies and Lockfiles

* Add a dependency only when necessary and no suitable built-in or existing solution exists. First explain the need, current-tool gap, and security or maintenance concerns.
* Avoid large dependencies for small problems. Do not change package managers unless requested.
* Change lockfiles only for intentional dependency changes.

## Command, Git, and File Safety

* Do not run destructive commands without explicit approval. Treat recursive deletion or moves, permission or ownership changes, and system configuration as high-risk.
* Do not run destructive Git operations such as `git reset --hard`, `git clean -fd`, force pushes, or branch deletion unless explicitly requested.
* Do not commit or push. Never discard or overwrite work to obtain a clean tree.

## Shared Security Rules

* Treat external and user-controlled data as untrusted; validate and sanitize at boundaries.
* Never weaken authentication, authorization, CSRF, CORS, validation, encryption, or rate limiting to make a feature work.
* Never expose stack traces, raw database errors, queries, schemas, tables, columns, or private implementation details to clients.
* Apply extra care to uploads, redirects, webhooks, payments, and admin-only behavior.

## Permission Required

Ask the user before the following actions. Approval does not override absolute prohibitions elsewhere in this file:

* Accessing or modifying sensitive data or configuration.
* Changing database data, applying migrations, or altering schemas. Required migration files may be created, but not applied without approval.
* Adding dependencies or changing package managers.
* Changing authentication, authorization, deployment, or production-related behavior.
* Deleting files, making large architectural changes, or running destructive commands.
* Changing payment, billing, webhook, or admin logic.

## Communication and Handoff

State assumptions, risks, tradeoffs, and uncertainty. Summarize changes, touched files, tests run and not run, remaining risks, and follow-up work.
