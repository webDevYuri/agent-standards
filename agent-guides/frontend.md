<!--
This guide applies to frontend components, state, rendering, data fetching,
navigation, browser behavior, security, performance, and framework-specific code.
Visual and UX work is routed from here to the dedicated UI/UX standards.
-->

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

* Keep components focused, readable, and easy to test.
* Separate presentation, state, data access, and business rules in proportion to application complexity.
* Preserve established project conventions. In a new project, use framework-standard patterns and add structure only when current requirements justify it.

## React and Next.js

* Preserve clear server and client component boundaries.
* Do not move logic or data fetching to the client unless browser execution is necessary.
* Follow configured loading, error, caching, form, and navigation patterns.
* Avoid unnecessary effects, duplicate state, and preventable re-renders.

## Angular

* Keep components, services, guards, interceptors, and modules in their established roles; keep complex logic out of templates.
* Use configured dependency injection, forms, and observable patterns.

## Vue and Nuxt

* Use one established Composition API or Options API style consistently; do not mix styles without a clear need.
* Keep reusable stateful logic in focused composables and visual structure in components.
* In Nuxt, preserve server and client boundaries and use its configured data-fetching, routing, and rendering patterns.

## Svelte and SvelteKit

* Keep state close to where it is used, derive values instead of synchronizing duplicate state, and reserve effects for external side effects.
* In SvelteKit, follow its load, form action, routing, and server-module patterns; keep secrets and server-only logic out of browser code.

## Astro

* Prefer static or server-rendered HTML by default and hydrate only components that require browser interactivity.
* Choose client directives deliberately, keep islands focused, and avoid shipping framework JavaScript for static content.
* Keep frontmatter and server-only logic separate from scripts that run in the browser.

## Other Frontend Frameworks

* Apply the shared frontend rules and use established project conventions or, for a new project, the framework's standard patterns.

## UI and UX Routing

* Before creating UI, inspect existing components, design tokens, patterns, and installed UI libraries.
* Visual or UX changes must load relevant [`uiux-ds.md`](uiux-ds.md#section-routing) sections; non-visual frontend work must not.

## Navigation and URLs

* Use established, predictable routes based on user-facing concepts; in a new project, use concise, consistent, readable segments without unclear abbreviations.
* Never put secrets, sensitive data, or unnecessarily revealing internal identifiers in URLs.
* When routes change, update affected navigation, links, tests, and examples.

## State, APIs, and Browser Security

### State and Rendering

* Avoid unnecessary global state. Handle loading, empty, error, retry, expired-session, and duplicate-submission behavior deliberately.

### Data Fetching and API Contracts

* Preserve established contracts. For new or changed contracts, read backend [API Design and Contracts](backend.md#api-design-and-contracts) and keep both sides aligned.
* Translate backend codes into safe, actionable user messages; never show raw server or database errors.

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

Run relevant unit, component, integration, end-to-end, type, lint, and local-build checks. Test affected API success and failure paths locally in the browser. For visual work, complete the UI/UX [Final Design Review](uiux-ds.md#final-design-review).
