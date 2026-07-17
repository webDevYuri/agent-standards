<!-- Backend guidance for APIs, data, security, integrations, and server configuration. -->

# Backend Development Guide

## Section Routing

* **Controller, service, queue, or job structure:** [Architecture and Code Style](#architecture-and-code-style), plus the applicable framework section when present.
* **Route, contract, status, or response:** [API Design and Contracts](#api-design-and-contracts).
* **Authentication, authorization, ownership, or privileged behavior:** [Authentication and Authorization](#authentication-and-authorization) and, when relevant, [Backend Security](#backend-security).
* **Input, upload, error, or abuse protection:** [Validation, Errors, and Abuse Protection](#validation-errors-and-abuse-protection).
* **New endpoint, endpoint bug, or runtime change:** The relevant API sections and [API Endpoint Verification](#api-endpoint-verification); add [Postman Collection](#postman-collection) when one exists.
* **Query, model, write, or transaction:** [Database Safety](#database-safety).
* **Migration:** [Database Safety](#database-safety) and [Migration Rules](#migration-rules).
* **Webhook or server integration:** [Backend Security](#backend-security), plus relevant API sections when endpoint-facing.
* **Server configuration:** [Server Configuration](#server-configuration) and [Backend Security](#backend-security), plus [Verification](#verification) when behavior changes.
* **Backend checks:** The affected section and [Verification](#verification).
* **Frontend-consumed contract:** Also read frontend [Data Fetching and API Contracts](frontend.md#data-fetching-and-api-contracts).

## Architecture and Code Style

* Keep controllers and route handlers focused on transport. Place validation, authorization, business logic, queues, and jobs in their established layers.
* Preserve established framework conventions. In a new project, use framework-standard patterns and add layers only when current requirements justify them.

## Laravel

* Use Form Requests for validation when appropriate.
* Use Policies, Gates, Middleware, Resources, Services, Jobs, and Events where they fit established architecture.

## Node.js and Express

* Use established controllers, services, middleware, validators, asynchronous behavior, and error handling.

## API Endpoints

### API Design and Contracts

* Keep the API cohesive and minimal. Prefer resource-oriented routes, extending a suitable endpoint, or query parameters; never combine unrelated operations or weaken HTTP semantics to reduce route count.
* Return the correct status, including `429 Too Many Requests` for rate limits. Never encode an error only in a successful response body.
* Preserve established response and pagination formats. Return safe, useful errors with a human-readable `message` and stable machine `code`; for a new API, use descriptive uppercase snake case such as `OTP_RESEND_NOT_READY`.
* Include retry timing, timestamps, flow context, or state flags only when clients need them. Expose public identifiers deliberately and consistently, never privileged or implementation-only identifiers.
* Coordinate client-visible contract changes with the frontend and update affected tests or documentation.

### Authentication and Authorization

* Apply authentication middleware when required and authorization checks wherever permissions or resource ownership matter.
* Keep privileged operations server-side; frontend checks are not security controls.

### Validation, Errors, and Abuse Protection

* Validate every used parameter, body field, header, and upload. Apply rate limits where abuse is possible.
* Handle missing records, invalid input, unauthorized access, duplicates, expired tokens, and upstream failures safely through the project’s error format.

## API Endpoint Verification

* Verify every new endpoint locally, even when simple. Endpoint bugs and runtime changes require targeted local verification; strictly non-behavioral changes may skip execution.
* Never verify an endpoint against a remote environment. Follow testing [Section Routing](testing.md#section-routing).

## Postman Collection

When a Postman collection exists, maintain it as part of the API; it supplements but never replaces [local endpoint verification](#api-endpoint-verification).

* Update changed, added, renamed, or removed endpoints, including URLs, methods, headers, authorization, parameters, payloads, and examples.
* Organize by resource or feature with descriptive scenario names, local sample fields, brief prerequisites, expected results, and minimal setup.
* Match the contract: `form-data` for multipart or uploads, raw JSON for `application/json`, and URL encoding only when required. Let Postman generate multipart boundaries.
* Keep a happy path for each endpoint. Add focused auth, validation, or failure cases only when useful. Saved error or business-state examples must include expected status and full response payload with `message`, `code`, and relevant context; tests must assert status and `code`.
* Use variables only for values that vary. Keep committed values empty or fake; never store credentials, tokens, personal data, or private URLs.
* Keep scripts short and transparent; carry only necessary temporary sequence values and avoid automation that obscures manual testing.

## Database Safety

* Use only local or isolated test databases for database work.
* Prefer migrations, seeders, factories, fixtures, and local test data to manual edits.
* Never run destructive operations without explicit confirmation, including `migrate:fresh`, `db:wipe`, `DROP`, `TRUNCATE`, and bulk `DELETE` or `UPDATE` statements.
* Avoid unbounded or N+1 queries, unnecessary round trips, and oversized results.
* Use transactions or established concurrency controls for atomic multi-step writes.

## Migration Rules

* In an established project, create a new migration instead of editing history. Edit an old migration only in clearly early development with user approval.
* Make migrations reversible when possible; review rollback behavior, defaults, nullability, indexes, foreign keys, and existing-data compatibility.

## Backend Security

* Verify webhook signatures and replay protections using the established approach when present, or the provider/framework-supported secure approach for a new integration.

## Server Configuration

* Preserve established configuration patterns and safe defaults. Keep secrets out of committed files and client-visible output.
* Make environment, deployment, or infrastructure behavior changes only when explicitly authorized, and verify them in a safe local or isolated environment.

## Verification

Run relevant unit, integration, feature, static-analysis, type, and lint checks. Check migrations only against an isolated local or test database. Endpoint execution follows [API Endpoint Verification](#api-endpoint-verification).
