<!-- Backend guidance for APIs, data, security, integrations, and server configuration. -->

# Backend Development Guide

## Section Routing

* **Controller, service, queue, or job structure:** [Architecture and Code Style](#architecture-and-code-style), plus the applicable framework section when present.
* **Route, contract, status, or response:** [API Design and Contracts](#api-design-and-contracts).
* **Authentication, authorization, ownership, or privileged behavior:** [Authentication and Authorization](#authentication-and-authorization) and, when relevant, [Backend Security](#backend-security).
* **Input, upload, error, or abuse protection:** [Validation, Errors, and Abuse Protection](#validation-errors-and-abuse-protection).
* **New endpoint, endpoint bug, or runtime change:** The relevant API sections and [API Endpoint Verification](#api-endpoint-verification); add [Postman Collection](#postman-collection) when one exists.
* **Query, model, write, or transaction:** [Database Safety](#database-safety).
* **Schema or migration:** [Domain and Schema Design](#domain-and-schema-design), [Database Safety](#database-safety), and [Migration Rules](#migration-rules).
* **Webhook or server integration:** [Backend Security](#backend-security), plus relevant API sections when endpoint-facing.
* **Server configuration:** [Server Configuration](#server-configuration) and [Backend Security](#backend-security), plus [Verification](#verification) when behavior changes.
* **Backend checks:** The affected section and [Verification](#verification).
* **Frontend-consumed contract:** Also read frontend [Data Fetching and API Contracts](frontend.md#data-fetching-and-api-contracts).

## Architecture and Code Style

* Keep transport handling focused and business rules under clear ownership in established layers. Simple behavior can stay simple; extract layers only for actual complexity, reuse, or responsibility boundaries.

## Laravel

* Use Form Requests, Policies, Gates, Middleware, Resources, Services, Jobs, and Events where appropriate to established architecture.

## Node.js and Express

* Use established controllers, services, middleware, validators, asynchronous behavior, and error handling.

## API Endpoints

### API Design and Contracts

* Use domain resources and HTTP methods predictably; explicit commands are appropriate for workflows that do not fit CRUD. Extend suitable endpoints without combining unrelated operations or exposing implementation details.
* Use correct statuses, including `429` for rate limits; never encode failure only in a successful response body.
* Preserve response and pagination conventions. Errors need a safe `message` and stable machine `code`; new APIs use descriptive uppercase snake case.
* Bound collections; support filtering, sorting, and pagination as needed. Include public identifiers, retry timing, or state context only when clients need them.
* Coordinate contract changes with consumers, tests, documentation, and existing Postman collections. Add versioning only for a demonstrated compatibility need.

### Authentication and Authorization

* Authentication establishes identity; separately authorize each relevant action and resource, including ownership and tenant boundaries. Frontend checks are not security controls.
* Derive authoritative roles, prices, ownership, calculated values, and allowed state transitions on the server; do not trust client assertions.

### Validation, Errors, and Abuse Protection

* Validate used parameters, fields, headers, and uploads at boundaries; allowlist writable fields and rate-limit abuse-prone operations.
* Validate upload type, size, and storage; constrain redirects or outbound destinations when user-controlled.
* Handle missing records, invalid input, unauthorized access, duplicates, expired tokens, and upstream failures safely through the project’s error format.

## API Endpoint Verification

* Verify every new endpoint locally, even when simple. Endpoint bugs and runtime changes require targeted local verification; strictly non-behavioral changes may skip execution.
* Never verify an endpoint against a remote environment. Follow testing [Section Routing](testing.md#section-routing).

## Postman Collection

Maintain an existing collection with the API; it never replaces [local endpoint verification](#api-endpoint-verification).

* Update affected URLs, methods, headers, auth, parameters, payloads, and examples. Group by resource or feature with descriptive scenario names, brief prerequisites, expected results, and safe local samples; avoid hidden sequencing.
* Match the contract: multipart `form-data` for uploads, raw JSON for `application/json`, URL encoding only when required. Let Postman generate multipart boundaries.
* Keep each endpoint's happy path and useful failure cases. Error/business-state examples need expected status and full payload with `message`, `code`, and relevant context; tests assert status and `code`.
* Use variables only for varying values; commit empty or fake values, never credentials, tokens, personal data, or private URLs. Keep scripts transparent and temporary sequence state minimal.

## Domain and Schema Design

* Model entities, cardinality, ownership, lifecycle, and invariants before columns. Choose domain-appropriate types, keys, nullability, and meaningful timestamps; enforce relational integrity and uniqueness with database constraints.
* Normalize for coherent ownership; store derived or denormalized data only for a concrete need with a consistency strategy. Do not normalize mechanically at the expense of common operations.
* Choose indexes for expected filtering, joins, sorting, and uniqueness, balancing query benefit against write and storage costs; use query evidence when optimizing.

## Database Safety

* Use only local or isolated test databases for database work.
* Prefer migrations, seeders, factories, fixtures, and local test data to manual edits.
* Never run destructive operations without explicit confirmation, including `migrate:fresh`, `db:wipe`, `DROP`, `TRUNCATE`, and bulk `DELETE` or `UPDATE` statements.
* Use parameterized queries. Avoid unbounded or N+1 queries, repeated round trips, unused columns, and inefficient scans; inspect access patterns before optimizing.
* Use transactions or concurrency controls as needed for multi-step or concurrent writes; handle retries or duplicate delivery idempotently where repeated effects matter.

## Migration Rules

* In an established project, create a new migration instead of editing history. Edit an old migration only in clearly early development with user approval.
* Review existing-data compatibility, defaults, nullability, keys, indexes, backfills, and locking risk. Make migrations reversible when possible; explain irreversible data loss and rollback limits. Applying them still requires user approval.

## Backend Security

* Verify webhook signatures and replay protections using the established approach when present, or the provider/framework-supported secure approach for a new integration.
* Prefer framework security mechanisms and context-appropriate output encoding over custom security code.

## Server Configuration

* Preserve established configuration patterns and safe defaults. Keep secrets out of committed files and client-visible output.
* Make environment, deployment, or infrastructure behavior changes only when explicitly authorized, and verify them in a safe local or isolated environment.

## Verification

Run relevant unit, integration, feature, static-analysis, type, and lint checks. Check migrations only against an isolated local or test database. Endpoint execution follows [API Endpoint Verification](#api-endpoint-verification).
