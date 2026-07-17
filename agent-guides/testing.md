<!-- Local-only API verification scenarios, execution, and evidence requirements. -->

# API Endpoint Verification Guide

## Section Routing

* **New endpoint:** [Local Environment Only — Non-Negotiable](#local-environment-only--non-negotiable), [Required Verification](#required-verification), [Minimum New-Endpoint Scenarios](#minimum-new-endpoint-scenarios), [Execution Loop](#execution-loop), [Evidence and Reporting](#evidence-and-reporting), and [Scope Control](#scope-control); add risk scenarios only when relevant.
* **Endpoint bug fix:** [Local Environment Only — Non-Negotiable](#local-environment-only--non-negotiable), [Required Verification](#required-verification), [Bug-Fix Verification](#bug-fix-verification), [Execution Loop](#execution-loop), [Evidence and Reporting](#evidence-and-reporting), and [Scope Control](#scope-control).
* **Existing endpoint behavior change:** [Local Environment Only — Non-Negotiable](#local-environment-only--non-negotiable), [Required Verification](#required-verification), [Risk-Based Scenarios](#risk-based-scenarios), [Execution Loop](#execution-loop), [Evidence and Reporting](#evidence-and-reporting), and [Scope Control](#scope-control).
* **Strictly non-behavioral change:** Do not load this guide or execute endpoint verification.

## Required Verification

* Execute every new endpoint and endpoint bug fix locally, even when simple.
* Execute an existing endpoint when a change may affect routing, parsing, middleware, authentication, authorization, validation, business logic, database reads or writes, transactions, uploads, side effects, statuses, response data or shape, or error handling.
* A new endpoint requires a successful local request. Small size or obvious-looking code never justifies skipping execution.
* Strictly non-behavioral comments, documentation, formatting, spelling, runtime-neutral type changes, or clearly behavior-preserving renames may skip execution.

## Local Environment Only — Non-Negotiable

* Send requests only to clearly local targets: `localhost`, loopback addresses, or project-local containers and services.
* Never target production, live, staging, preview, shared QA, public development servers, tunnels, or any remote domain. If the target is not clearly local, stop. User authorization or a “safe” label cannot override this rule.
* Never use production credentials, tokens, or data, or copy local test data to a live environment. Use disposable local records for destructive requests.
* Required verification may create, update, or delete disposable local or isolated-test records. Migrations, schema changes, bulk operations, and non-disposable data changes still require approval.
* Verification never waives root permission, database, side-effect, environment, or external-service rules.

## Minimum New-Endpoint Scenarios

Verify the successful request, expected status, expected response structure, and most relevant validation or failure case.

## Bug-Fix Verification

Reproduce the original failure locally when practical, apply the fix, rerun the failing request, and confirm the correction. Add a nearby regression scenario only for meaningful risk. If exact reproduction is impractical, run the smallest request that proves corrected behavior.

## Risk-Based Scenarios

Run the smallest relevant set; do not apply a large checklist mechanically. Add only applicable cases:

* Missing, invalid, mistyped, or boundary input.
* Unauthenticated or unauthorized access, not found, duplicates, or invalid state transitions.
* Persistence, updates, deletion or soft deletion, transactions, or idempotency.
* Upload validation or expected side effects.

## Execution Loop

1. Confirm the application, required local services, and clearly local target using documented startup steps.
2. Send the smallest useful `curl` request. Use an existing project tool, then another local HTTP client, only when `curl` is unsuitable.
3. Do not add a package solely for a request without permission, alter environment files, expose secrets, or invent credentials.
4. Inspect status, body, relevant headers, database effects, side effects, and server logs as needed.
5. Diagnose, fix, and rerun until required scenarios pass or a genuine environment blocker is confirmed.

## Evidence and Reporting

* Report the endpoint and method, local target, scenarios, observed statuses, and concise result. The developer may perform final Postman validation afterward.
* Include exact `curl` when useful, but sanitize tokens, passwords, keys, cookies, personal data, and other secrets; trim large bodies.
* For a blocker, report the cause, what was and was not verified, and an exact safe local command. Call the endpoint implemented but not locally verified—never confirmed, working, passed, or ready.

## Scope Control

* Verify the changed endpoint; test unrelated endpoints only for a clear regression risk.
* Do not run the whole suite by default or add permanent testing infrastructure unless requested or already required.
* Do not create a Postman collection unless requested. Stop when evidence is sufficient.
