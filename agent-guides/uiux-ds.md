<!-- UI/UX routing and project-level constraints. Impeccable owns design practice. -->

# UI/UX Routing

## Section Routing

Use the project-local Impeccable skill at `.agents/skills/impeccable/` as the primary UI/UX system. From the project root, run `.agents/skills/impeccable/scripts/impeccable.cmd context` once per session, inspect the target and existing visual system, load the referenced command playbook, and read its craft-floor guidance before editing UI. Use the minimum command set that matches the request; do not run every command by default. On shells that support it, the launcher may be invoked as `impeccable` instead of `impeccable.cmd`.

| Task | Impeccable command(s) |
| --- | --- |
| New page, flow, or major redesign | `shape` when UX direction needs planning; then the `new-work` workflow. Use `init` first only when product context is missing. |
| Improve an existing page or component | `critique`, then the narrowly relevant refinement command; finish with `polish`. |
| Final visual/UX review before handoff | `critique` for heuristic UX issues, `audit` for accessibility/performance/responsive issues, and `polish` to resolve the final findings. Select only the applicable review commands. |
| Typography or font hierarchy | `typeset` |
| Layout, spacing, rhythm, or hierarchy | `layout` |
| Responsive or device adaptation | `adapt` |
| Accessibility, technical UI quality, or performance | `audit` (use the native variant on native platforms); use `optimize` for performance-only work |
| Simplification or cognitive-load reduction | `distill`; use `clarify` when the issue is copy, labels, or errors |
| Errors, empty states, edge cases, i18n, or production readiness | `harden` |
| Onboarding or first-run experience | `onboard` |
| Motion or interaction feedback | `animate` |
| Color, personality, or visual intensity | `colorize`, `delight`, `bolder`, or `quieter` only when the request calls for that specific change |
| One-off visual alternatives in a running web app | `live` or `generate` |

Combine commands only when their purposes are distinct (for example, `critique` + `layout` + `polish`). Ask once when two commands are equally plausible. Treat a redesign as a replacement visual direction, not incremental polish; treat a focused refinement as preservation of the incumbent identity and behavior.

## Post-Implementation Refinement

For new pages, major redesigns, or substantial visual changes, do not treat the first completed implementation as the final design.

After the initial implementation:

1. Render and inspect the actual result at representative desktop and mobile viewport sizes. Review the rendered interface rather than judging from source code alone.

2. Perform a critical UI/UX evaluation of the complete result as an experienced product designer reviewing work before production handoff. Judge what is actually visible and usable, not what the implementation intended to achieve.

3. Identify meaningful weaknesses in the current result. Consider the interface holistically, including visual and information hierarchy, typography, readability, composition, spacing and rhythm, density, content presentation, imagery, consistency, interaction clarity, responsive adaptation, accessibility, and the effectiveness of the primary user journey. These are review dimensions, not a requirement to find a problem in every category.

4. Preserve successful decisions. Distinguish between intentional design choices and actual weaknesses. Do not redesign a strong direction merely to produce a different result, and do not invent issues to justify another iteration.

5. Convert the observed weaknesses into concise, evidence-based refinement feedback. Describe the problems and their effect on the experience without prescribing arbitrary visual solutions unless the solution is required by functionality, accessibility, or an explicit requirement.

6. Perform one focused refinement pass based on that feedback. Use only the Impeccable commands relevant to the findings. Improve the existing direction rather than restarting it unless the evaluation reveals a fundamental failure.

7. Render and inspect the refined result again at the affected viewport sizes, then continue to the applicable final review and verification.

The refinement pass is mandatory for substantial UI work when meaningful visual evaluation is possible. It is not required for minor styling fixes, narrowly scoped adjustments, or non-visual frontend work.

Limit this automatic refinement process to one pass. If the first implementation already withstands critical review and no meaningful improvement is identified, make no arbitrary changes and proceed to final verification.

## Project-Level Constraints

- Preserve existing functionality and product truth: actions, state, validation, API contracts, navigation, permissions, and loading/empty/error/success states.
- Inspect and reuse the existing design system, tokens, components, and installed UI libraries before creating alternatives. Do not install, replace, or materially reconfigure a UI library without explicit permission.
- Keep changes scoped to the requested surface. Avoid unrelated refactors, speculative design-system expansion, and unnecessary dependency or lockfile changes.
- Use realistic content and preserve meaningful distinctions such as missing, zero, empty, unknown, and error states. Do not invent claims, metrics, testimonials, or business data.
- Follow the project’s framework, accessibility, security, and browser conventions in `frontend.md`; Impeccable routing does not override them.
- Review the affected flow locally at relevant viewport sizes and with keyboard interaction when available. Report checks not run and remaining uncertainty; screenshots alone do not prove behavior or accessibility.