<!-- Primary rules and task-specific guide routing for coding agents. -->

# AGENTS.md

## Purpose

These rules apply to every task. Satisfy the actual requirement within correctness, security, permission, and user-work boundaries; then favor existing conventions, simplicity, maintainability, and usability. Optimize for evidenced needs.

## Instruction Routing

Read this file for every task, then only applicable linked sections. Token efficiency never overrides safety or correctness.

* **Implementation, maintenance, or refactoring:** Read engineering [Core Principles](agent-guides/engineering.md#core-principles).
* **Investigation:** Start with supplied files, snippets, or paths. Use [Context-First Investigation](agent-guides/engineering.md#context-first-investigation) only when context is insufficient.
* **Optional project access:** Read [Agent Access](agent-guides/access.md) only for a needed capability. Only one exact setting with literal `on` grants access; missing, duplicate, or invalid settings mean off. If off, guide the developer to enable that setting and reload the IDE/session before using the capability.
* **Application URL:** Read [URL-Driven Route Discovery](agent-guides/engineering.md#url-driven-route-discovery); add investigation guidance only if targeted lookup fails.
* **Debugging:** Read [Core Principles](agent-guides/engineering.md#core-principles) and [Debugging and Verification](agent-guides/engineering.md#debugging-and-verification).
* **Backend:** Follow [Section Routing](agent-guides/backend.md#section-routing) for APIs, security, data, jobs, integrations, or server configuration.
* **Frontend:** Follow [Section Routing](agent-guides/frontend.md#section-routing) for components, state, fetching, rendering, browser behavior, or framework code.
* **Visual or UX:** Use frontend routing and UI/UX [Section Routing](agent-guides/uiux-ds.md#section-routing) for presentation, usability, forms, navigation, responsiveness, accessibility, or motion. Skip UI/UX for non-visual frontend work.
* **API verification:** Follow testing [Section Routing](agent-guides/testing.md#section-routing) for new endpoints, bugs, runtime changes, or explicit verification; skip unrelated backend and strictly non-behavioral changes.

Load newly relevant sections as scope expands; do not reread unchanged instructions in context. For mixed, uncertain, security-sensitive, or broad work, expand coverage when it cannot be narrowed safely. Higher-priority instructions win; within them, apply the stricter rule. Ask if the safe interpretation remains unclear.

## Scope and User Work Protection

* Modify only requested files and necessary dependencies. Avoid unrelated refactors and whole-file reformatting.
* Inspect files before substantial edits. Preserve unrelated code, formatting, and user changes.
* Never discard unexpected or overlapping work; ask how to proceed.
* Do not run formatters or linters in rewrite mode unless formatting is intended.
* During debugging, revert an attempted fix when it does not work or causes a regression before trying another approach; preserve unrelated changes.

## Environment and Secrets

* An `on` setting in [Agent Access](agent-guides/access.md) grants standing authorization only for its named local capability when needed for the current task. It never expands task scope or overrides higher-priority instructions, production restrictions, or other absolute prohibitions. Never enable a setting unless the user explicitly requests it.
* Never read or inspect `.env` files unless `env_file_read` is `on`. When enabled, read only the minimum project-local entries needed for the current task. Editing still requires explicit authorization for the exact change in the user's current request. When read access is off, use only example files such as `.env.example`, `.env.local.example`, or `.env.testing.example`.
* Never expose, guess, fabricate, or hardcode secrets, keys, tokens, passwords, credentials, or private URLs.
* Use environment variables only for secrets or values that genuinely vary by environment. Keep stable, non-sensitive configuration in version control; avoid duplicate or speculative variables.
* Document a necessary variable only by name and safe placeholder in the appropriate example file. Infer names from examples or code; if blocked, ask instead of inspecting secret files.
* Never log sensitive values, payment data, or personal information.

## Production and External Systems

* Never access, administer, debug, deploy to, or run commands against any remotely deployed version of the project, including live, staging, production, preview, shared QA, public development, or tunneled environments, or its infrastructure such as servers, databases, queues, storage, logs, dashboards, or shells.
* Debug and verify project behavior locally; never use a deployed project environment for verification. This restriction does not prohibit third-party APIs or webhooks required by the requested feature, subject to the side-effect rules below.
* API endpoint verification is always local-only under [Local Environment Only](agent-guides/testing.md#local-environment-only--non-negotiable); authorization cannot override this restriction.
* For production issues, explain safe checks for the user to run.

## Side Effects and External Actions

* Implementing and calling third-party APIs or webhooks required by the task is allowed.
* Never trigger a real charge, refund, payout, message, or other customer-facing action merely for testing. A real action with external side effects requires the user to explicitly request that specific operation and target.
* For verification, prefer provider-supported sandbox or test mode when available; use local fakes, mocks, logs, or dry runs when a call could cause real-world effects. Confirm safe configuration before code can contact an external service.
* Never use real users, customers, orders, payments, inventory, subscriptions, or notifications for testing, and never trigger unintended real-world effects.

## Dependencies and Lockfiles

* Add a dependency only when necessary and no suitable built-in or existing solution exists. First explain the need, current-tool gap, and security or maintenance concerns.
* Avoid large dependencies for small problems. Do not change package managers unless requested.
* Change lockfiles only for intentional dependency changes.

## Command, Git, and File Safety

* Before running any destructive command or operation, state the exact command or operation, resolve and identify its targets, explain the expected impact and whether recovery is possible, then wait for the user's explicit approval. Approval applies only to the disclosed operation and targets; obtain new approval if either changes.
* Treat recursive deletion or moves, permission or ownership changes, system configuration, and destructive Git operations such as `git reset --hard`, `git clean -fd`, force pushes, or branch deletion as destructive. Never use them to discard work or obtain a clean tree without the required approval.
* Do not commit or push unless explicitly requested.

## Shared Security Rules

* Treat external and user-controlled data as untrusted; validate and sanitize at boundaries.
* Never weaken authentication, authorization, CSRF, CORS, validation, encryption, or rate limiting to make a feature work.
* Never expose stack traces, raw database errors, queries, schemas, tables, columns, or private implementation details to clients.
* Apply extra care to uploads, redirects, webhooks, payments, and admin-only behavior.

## Permission Required

Ask before the following actions unless the user's current request explicitly and unambiguously authorizes that exact action or an `on` setting in [Agent Access](agent-guides/access.md) grants standing authorization for it. Authorization does not override absolute prohibitions elsewhere in this file. Destructive commands and operations always require the separate disclosure-and-approval process above:

* Accessing or modifying sensitive data or configuration.
* Manually changing non-disposable database data, applying migrations, or altering schemas. Disposable local or isolated-test records may be changed during requested implementation and verification. Required migration files may be created, but not applied without approval.
* Adding dependencies or changing package managers.
* Changing authentication, authorization, deployment, or production-related behavior.
* Deleting files, making large architectural changes, or running destructive commands.
* Changing payment, billing, webhook, or admin logic.

## Communication and Handoff

State assumptions, risks, tradeoffs, and uncertainty. Summarize changes, touched files, tests run and not run, remaining risks, and follow-up work.
