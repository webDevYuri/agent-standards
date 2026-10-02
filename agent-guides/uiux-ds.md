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

This stage is a **design-quality critique and refinement pass**. It is separate from mechanical UI detectors, accessibility audits, technical verification, automated checks, and the final Impeccable reviewer. Those checks may inform later verification, but they do not satisfy or replace this stage.

After the initial implementation:

1. **Render the actual result.** Inspect the completed interface at representative desktop and mobile viewport sizes. Evaluate the rendered experience rather than judging from source code or implementation intent.

2. **Critique the design itself.** Review the result as a highly experienced product/UI/UX designer deciding whether the work has reached the strongest reasonable version of its current direction. Evaluate the interface as a complete experience, not as a checklist of technical requirements.

3. **Judge what could meaningfully be better.** Look for weaknesses in visual and information hierarchy, typography, readability, composition, spacing and rhythm, density, content presentation, imagery, consistency, interaction clarity, responsive composition, and the effectiveness of the primary user journey. Consider other design issues when they are visible in the result.

4. **Separate design critique from QA findings.** Overflow bugs, contrast violations, undersized targets, missing states, accessibility failures, broken interactions, and similar technical findings still need correction, but fixing them alone does not count as the design refinement pass. The purpose of this stage is to determine whether the interface itself can be meaningfully improved beyond being correct and compliant.

5. **Preserve what works.** Identify successful decisions as well as weaknesses. Do not redesign a strong direction merely to create visible change. Do not invent issues or force an iteration when the current design already withstands critical review.

6. **Create refinement feedback from the rendered result.** When meaningful improvements exist, summarize the observed design weaknesses and their effect on the experience. Focus on problems and outcomes rather than prescribing arbitrary visual solutions.

7. **Perform one focused design refinement pass.** Apply the feedback using only the relevant Impeccable commands. Improve the existing direction rather than restarting it unless the critique reveals a fundamental design failure.

8. **Inspect the refined result again.** Re-render the affected desktop and mobile views and judge whether the identified design weaknesses were actually improved. Then proceed separately to the applicable audits, technical verification, and final review.

For substantial UI work, the **design critique is mandatory** when meaningful visual inspection is possible. A design change is not mandatory: if the implementation already withstands critical design review and no meaningful improvement is identified, explicitly record that conclusion and proceed without arbitrary changes.

Limit this automatic design refinement to one pass. Final QA, accessibility checks, detectors, and independent review may still require fixes afterward, but those fixes are verification work rather than another automatic design iteration.

## Project-Level Constraints

- Preserve existing functionality and product truth: actions, state, validation, API contracts, navigation, permissions, and loading/empty/error/success states.
- Inspect and reuse the existing design system, tokens, components, and installed UI libraries before creating alternatives. Do not install, replace, or materially reconfigure a UI library without explicit permission.
- Keep changes scoped to the requested surface. Avoid unrelated refactors, speculative design-system expansion, and unnecessary dependency or lockfile changes.
- Use realistic content and preserve meaningful distinctions such as missing, zero, empty, unknown, and error states. Do not invent claims, metrics, testimonials, or business data.
- Follow the project’s framework, accessibility, security, and browser conventions in `frontend.md`; Impeccable routing does not override them.
- Review the affected flow locally at relevant viewport sizes and with keyboard interaction when available. Report checks not run and remaining uncertainty; screenshots alone do not prove behavior or accessibility.