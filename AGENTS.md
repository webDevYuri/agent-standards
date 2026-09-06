<!-- Primary rules and task-specific guide routing for coding agents. -->

# AGENTS.md

## Purpose

These rules apply to every task. Prioritize correctness, security, permissions, maintainability, and preservation of user work.

## Instruction Routing

Read this file for every task. Classify the request and affected paths, then load only the linked sections that apply. Token efficiency never overrides correctness, security, permissions, production or data safety, or preservation of user work.

* **Implementation, maintenance, or refactoring:** Read engineering [Core Principles](agent-guides/engineering.md#core-principles).
* **User-provided files, snippets, or exact paths:** Start there. Load [Context-First Investigation](agent-guides/engineering.md#context-first-investigation) only if that context is insufficient.
* **Optional project access:** Read [Agent Access](agent-guides/access.md) only when a task requires a capability it controls. A missing file, missing setting, or any value other than literal `on` means `off`. If the required access is off or not recognized, guide the developer to set the exact setting to `on` and reload the IDE/session before continuing.
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
