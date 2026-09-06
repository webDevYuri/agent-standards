<!-- Frontend guidance for framework code, browser behavior, security, and verification. -->

# Frontend Development Guide

## Section Routing

* **Component structure or logic:** [Architecture and Code Style](#architecture-and-code-style), plus the applicable framework section.
* **State or rendering:** [State and Rendering](#state-and-rendering), plus the applicable framework section.
* **Data fetching or API consumption:** [Data Fetching and API Contracts](#data-fetching-and-api-contracts).
* **API contract change:** [Data Fetching and API Contracts](#data-fetching-and-api-contracts), backend [API Design and Contracts](backend.md#api-design-and-contracts), and [Postman Collection](backend.md#postman-collection) when one exists.
* **Browser security:** [Browser Security](#browser-security).
* **Navigation or URL:** [Navigation and URLs](#navigation-and-urls); add UI/UX routing when presentation or user flow changes.
* **Visual, responsive, interaction, or accessibility work:** [UI and UX Routing](#ui-and-ux-routing), the relevant implementation section, and UI/UX [Section Routing](uiux-ds.md#section-routing).
* **Performance or checks:** [Performance and Maintainability](#performance-and-maintainability) or [Verification](#verification), plus the affected section.

## Architecture and Code Style

* Give components clear responsibilities; separate complex state, data access, and business rules when useful. Avoid both giant components and fragmenting simple views without a reuse or responsibility benefit.
* Follow project conventions; in a new project, add only framework-standard structure needed now.

## React and Next.js

* Preserve server/client boundaries; move logic or fetching to the client only when browser execution is needed. Follow configured loading, error, caching, form, and navigation patterns.

## Angular

* Keep components, services, guards, interceptors, and modules in their established roles; keep complex logic out of templates.
* Use configured dependency injection, forms, and observable patterns.

## Vue and Nuxt

* Follow the established Composition API or Options API style. Keep reusable stateful logic in focused composables and visuals in components.
* In Nuxt, preserve server/client boundaries and configured fetching, routing, and rendering patterns.

## Svelte and SvelteKit

* In SvelteKit, follow load, form action, routing, and server-module patterns; keep server-only logic out of browser code.

## Astro

* Prefer static/server-rendered HTML; hydrate only interactive islands with appropriate client directives. Keep frontmatter and server-only logic separate from browser scripts.

## UI and UX Routing

* Visual or UX changes must load relevant [`uiux-ds.md`](uiux-ds.md#section-routing) sections; non-visual frontend work must not.

## Navigation and URLs

* Use predictable routes based on user-facing concepts, with consistent readable segments.
* Never put secrets, sensitive data, or unnecessarily revealing internal identifiers in URLs.
* When routes change, update affected navigation, links, tests, and examples.

## State, APIs, and Browser Security

### State and Rendering

* Keep one authoritative owner for each state near its consumers; derive values instead of synchronizing duplicates. Use global state only for genuinely shared needs and effects for external synchronization.
* Handle relevant loading, empty, success, error, retry, expired-session, and duplicate-submission behavior. Preserve input on recoverable failures; prevent stale responses or races from overwriting newer state.

### Data Fetching and API Contracts

* Preserve established contracts. For new or changed contracts, read backend [API Design and Contracts](backend.md#api-design-and-contracts) and keep both sides aligned.
* Translate backend codes into safe, actionable user messages; never show raw server or database errors.
* Use client validation for feedback and server validation for correctness. Reconcile mutations with authoritative data; use optimistic updates only with clear failure recovery.

### Browser Security

* Do not rely on client-side checks for authentication, authorization, validation, or access control.
* Never place secrets in frontend code, browser storage, logs, or analytics.
* Avoid unsafe HTML insertion; when unavoidable, use established or framework-supported sanitization.
* Never weaken CSRF, content security, or secure cookies to make a feature work.

## Performance and Maintainability

* Avoid unnecessary re-renders, repeated API calls, and oversized client bundles.
* Use lazy loading, memoization, or caching only for a measured need or established pattern.
* Keep payloads appropriate to the view; do not fetch unused data.

## Verification

Run relevant unit, component, integration, end-to-end, type, lint, and local-build checks. For frontend API work, verify affected UI success and failure behavior against a clearly local API or the project's established test setup. For visual work, complete the UI/UX [Final Design Review](uiux-ds.md#final-design-review).
