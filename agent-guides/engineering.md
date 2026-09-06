<!-- Engineering principles for implementation, investigation, debugging, and verification. -->

# Engineering Guide

## Section Routing

* **Implementation, maintenance, or refactoring:** [Core Principles](#core-principles).
* **Missing files, unknown implementation, or insufficient supplied context:** [Context-First Investigation](#context-first-investigation).
* **Application URL supplied instead of files:** [URL-Driven Route Discovery](#url-driven-route-discovery); add [Context-First Investigation](#context-first-investigation) only if route discovery requires broader search.
* **Debugging:** [Core Principles](#core-principles) and [Debugging and Verification](#debugging-and-verification); add investigation guidance only when the cause or implementation is unknown.

## Core Principles

### Read Before Writing

* Establish the requirement and expected behavior; inspect relevant architecture, conventions, constraints, and data flow before editing.
* Distinguish observed facts, user requirements, inferences, and assumptions. Resolve uncertainty from available context; ask only for material unresolved ambiguity or required permission. Proceed on safe, reversible choices within scope.

### Prefer the Simplest Correct Solution

* Satisfy known requirements with clear, secure, testable code whose maintenance cost is justified. Avoid speculative features, configuration, fallback behavior, infrastructure, and extensibility.
* Use the existing stack. Optimize for measured problems, predictable high-impact risks, or obvious inefficiency.

### Reuse Before Creating

* Reuse suitable implementations and extend established patterns without forcing unsafe or confusing coupling.
* Add abstractions or layers only for demonstrated complexity, meaningful reuse, or a responsibility boundary, including a justified single use. Keep responsibilities cohesive and dependencies clear.

### Preserve Existing Behavior

* Keep diffs focused; preserve required compatibility and behavior outside the request. Refactor only to implement safely or resolve an immediate task-related problem.
* Simplify or remove what the current change makes obsolete, including unused imports and temporary artifacts; obey root deletion permissions. Leave unrelated cleanup, renaming, formatting, and modernization alone.

### Consistency Over Personal Preference

* Follow established architecture, naming, folders, validation, and error handling. Keep files cohesive; avoid duplicate or catch-all structures.
* In new projects, use conventional foundations needed now. If an existing pattern is unsafe or unsuitable, explain why and make the smallest justified correction.
* Prefer predictable, readable code and descriptive names. Comment non-obvious intent, constraints, business rules, or tradeoffs; avoid narration and unnecessary documentation.

### Verify and Stop

* Verify behavior and important boundaries with existing tests and configured local checks, scaled to risk; use stronger coverage for permissions, money, persistence, migrations, and critical workflows. Complete required checks and routed verification.
* Fix failures caused by the change; report unrelated failures, blockers, and unverified behavior. Never claim unexecuted checks or unobserved behavior passed.
* Stop when the requested behavior and required verification are complete; do not add adjacent improvements.

## Context-First Investigation

* Inspect user-provided files, paths, snippets, logs, stack traces, screenshots, and implementation context first. Do not search when they are sufficient.
* Search when relevant files are absent, the implementation or cause is unknown, a dependency must be located, the change directly affects other files, or the user requests broader investigation.
* Start with exact filenames, identifiers, routes, endpoint or component names, errors, tables, methods, or imported symbols. Open a small candidate set.
* Expand only as needed and stop when enough context exists to implement and verify safely. Do not scan the repository or open unrelated files by default.
* Use built-in filename, text, symbol, reference, and semantic search when available. Do not build indexing, embeddings, AST, dependency-graph, or search infrastructure merely to locate files.

## URL-Driven Route Discovery

1. Extract the route path; ignore the domain, query, and fragment unless they affect routing or the reported behavior.
2. Classify it as a frontend, API, admin, server-rendered, or other application route.
3. Locate the route definition before lower-level files. For file-based routing, match the page, layout, loader, action, or handler, including dynamic parameters, nesting, route groups, and optional segments.
4. For explicit routing, find registration before its controller, handler, component, service, validation, middleware, or policy.
5. Follow only directly connected files and calls. Expand search only if targeted route lookup fails.
6. Stop when the relevant request or render flow is understood.

## Debugging and Verification

* Compare expected and observed behavior; reproduce the smallest practical failure before fixing it.
* Trace the relevant input, validation, business logic, persistence, response/state, and presentation until evidence identifies the responsible layer. Scale investigation to uncertainty; obvious bugs need no architectural survey.
* Correct the cause at that layer instead of hiding symptoms downstream. Revert ineffective attempts or regressions before another approach, preserving unrelated work.
* Rerun the reproduction and meaningful nearby regression checks. If exact reproduction is impractical, use the smallest check that demonstrates corrected behavior and disclose the limit.
* Remove temporary diagnostics unless they provide lasting value; follow Core verification and stop criteria.
