# Frontend Development Guide

## Section Routing

* **Component structure or logic:** [Architecture and Code Style](#architecture-and-code-style) and the applicable [React and Next.js](#react-and-nextjs) or [Angular](#angular) section.
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

## React and Next.js

* Preserve clear server and client component boundaries.
* Do not move logic or data fetching to the client unless browser execution is necessary.
* Follow configured loading, error, caching, form, and navigation patterns; otherwise use framework-standard behavior.
* Avoid unnecessary effects, duplicate state, and preventable re-renders.

## Angular

* Keep components, services, guards, interceptors, and modules in their established roles; keep complex logic out of templates.
* Use configured dependency injection, forms, and observable patterns, or Angular standards in a new project.

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
