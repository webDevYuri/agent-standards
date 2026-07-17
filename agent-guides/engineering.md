<!-- Engineering principles for implementation, investigation, debugging, and verification. -->

# Engineering Guide

## Section Routing

* **Implementation, maintenance, or refactoring:** [Core Principles](#core-principles).
* **Missing files, unknown implementation, or insufficient supplied context:** [Context-First Investigation](#context-first-investigation).
* **Application URL supplied instead of files:** [URL-Driven Route Discovery](#url-driven-route-discovery); add [Context-First Investigation](#context-first-investigation) only if route discovery requires broader search.
* **Debugging:** [Core Principles](#core-principles) and [Debugging and Verification](#debugging-and-verification); add investigation guidance only when the cause or implementation is unknown.

## Core Principles

### Delete Before Adding

* Remove, simplify, consolidate, or replace unnecessary code before adding more. Remove obsolete compatibility layers, helpers, and abstractions, but keep working behavior and compatibility required by the current scope.

### Reuse Before Creating

* Find and reuse a suitable existing implementation, utility, service, component, middleware, validator, type, pattern, or convention.
* Do not force unrelated, unsafe, or confusing coupling.

### Extend Before Abstracting

* Extend an established pattern before adding an abstraction.
* Add wrappers, factories, base classes, generic helpers, or framework-like layers only for current duplication or demonstrated structural need, never a single or hypothetical use case.

### Solve the Current Requirement

* Implement only the current requirement. Do not add speculative features, configuration, extensibility, fallback behavior, future-proofing, or adjacent improvements.

### Prefer the Simplest Correct Solution

* Choose the correct solution that is easiest to understand, verify, and maintain.
* Prefer explicit, conventional code; avoid unnecessary files, layers, indirection, dependencies, moving parts, duplication, and obvious inefficiency.

### Every Addition Has a Cost

* Add lines, files, abstractions, dependencies, configuration, or integrations only when the current requirement justifies their maintenance cost.
* Use the existing stack when it can reasonably provide the needed behavior.

### Read Before Writing

* Read enough relevant requirements, code, architecture, conventions, and data flow to avoid assumptions and make a safe change.
* Ask before proceeding when uncertainty creates risk or could materially change the result.

### Preserve Existing Behavior

* Preserve behavior outside the request; do not rewrite working code because another approach appears cleaner.
* Avoid unrelated cleanup, renaming, formatting, restructuring, or modernization. Keep diffs focused and reviewable.

### Refactor Only When It Helps the Task

* Refactor only when required for a safe implementation or to remove an immediate problem.
* Do not turn feature or bug-fix work into a broad refactor; separate optional cleanup from behavioral changes when practical.

### Consistency Over Personal Preference

* Follow established architecture, naming, folders, error handling, validation, and coding conventions rather than personal preference.
* In a new or mostly empty project, use simple, widely understood conventions and add only foundations needed now; keep early choices easy to extend or replace.
* If an established pattern is unsafe or unsuitable, explain why and make the smallest justified correction.

### Prefer Predictable Code

* Prefer conventional, readable code over clever or compressed code.
* Use descriptive names; abbreviate only when standard and unambiguous.
* Comment only non-obvious intent, constraints, or tradeoffs. Do not narrate clear code.

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

* Identify the cause before changing code; prefer a targeted fix over trial-and-error or broad rewrites.
* Remove temporary logs unless they provide lasting value.
* Run relevant configured local checks.
* Never claim unexecuted checks or unobserved behavior passed.
