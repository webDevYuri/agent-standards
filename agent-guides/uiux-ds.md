<!-- UI/UX standards for consistent, accessible, responsive, and purposeful interfaces. -->

# UI/UX Design Standards

## Section Routing

**Baseline for every UI/UX task:** [Preserve Functionality](#preserve-functionality), [Existing Design System First](#existing-design-system-first), and [Final Design Review](#final-design-review). Add the sections below; load overlapping sections only once.

* **New screen or substantial redesign:** [Design Workflow](#design-workflow) through [Components and Content](#components-and-content), [Interaction States](#interaction-states), [Responsive Design](#responsive-design), [Accessibility](#accessibility), and [AI-Slop Prevention](#ai-slop-prevention); add forms/data and motion when relevant.
* **Existing component styling:** The affected layout, typography, spacing, or color sections; [Interaction States](#interaction-states) and [Accessibility](#accessibility); add responsive guidance when affected.
* **Forms, tables, or dashboards:** [Layout and Visual Hierarchy](#layout-and-visual-hierarchy), [Components and Content](#components-and-content), [Forms and Data-Dense Interfaces](#forms-and-data-dense-interfaces), [Interaction States](#interaction-states), [Responsive Design](#responsive-design), and [Accessibility](#accessibility); add screen-design guidance for a new screen or substantial redesign.
* **Responsive or accessibility fix:** The directly relevant [Responsive Design](#responsive-design) or [Accessibility](#accessibility), and affected [Interaction States](#interaction-states).
* **Animation or feedback:** [Interaction States](#interaction-states), [Motion and Feedback](#motion-and-feedback), and [Accessibility](#accessibility).
* **Marketing or template-risk review:** [Understand the Product Before Designing](#understand-the-product-before-designing), [Design Direction](#design-direction), [Layout and Visual Hierarchy](#layout-and-visual-hierarchy), [Components and Content](#components-and-content), and [AI-Slop Prevention](#ai-slop-prevention).

## Preserve Functionality

* Before visual changes, identify affected actions, handlers, state, validation, API contracts, navigation, and permissions; preserve their behavior unless the task explicitly requires a change.
* Do not remove features, hide essential actions, replace functioning controls with static mockups, or drop loading, empty, error, disabled, or success states to simplify a layout. Keep essential actions discoverable across screen sizes.
* Identify proposed behavior changes and their impact separately before implementation. Unrequested workflow or business-rule changes require clarification; visual cleanup does not authorize them.

## Design Workflow

For new screens and substantial redesigns, use four steps, scaled to scope:

1. **Understand:** Identify the user, main task, content, constraints, and existing flow from supplied context and relevant implementation.
2. **Choose direction:** Establish information order, layout, density, typography, and color roles from the product, brand, or references. Briefly state material assumptions; ask only when unresolved choices affect scope or behavior.
3. **Build:** Reuse components and tokens; implement relevant states and responsive behavior alongside the layout.
4. **Review:** Walk through the affected task locally, inspect the rendered result, and refine observed problems using [Final Design Review](#final-design-review).

Small fixes need only affected decisions and checks; do not require a separate design document, multiple concepts, or approval ceremony for routine reversible work.

## Understand the Product Before Designing

* Start from the actual product, audience, task, context, and likely errors. Make needed information and the next action discoverable; minimize unnecessary decisions and effort without hiding consequences.
* Match familiar product flows and language. Use recognition over recall; reveal secondary detail when needed without hiding essential controls. Adapt to user experience only where justified.
* Treat psychology as contextual hypotheses, not guaranteed conversion tactics. Preserve informed choices, honest progress, and easy refusal or cancellation; never use deception or obstructive defaults.
* These are design defaults, not a visual style. Deviate for a clear product, brand, accessibility, or usability reason; in new projects, add only foundations needed now.

## Existing Design System First

* Inspect surrounding screens, branding, components, installed libraries, tokens, and interaction patterns before styling.
* Prefer project components, then suitable installed libraries, existing tokens/variants, and composition or extension; use custom UI only when these are unsuitable. Reuse accessible state and keyboard behavior without forcing awkward UX.
* Do not install or replace a UI library without permission. Keep styling within the existing system.

## Design Direction

* Use supplied references to identify relevant composition, hierarchy, typography, imagery, and interaction patterns. Honor requested fidelity; do not copy unrelated content or behavior.
* For a new visual system, choose a small coherent set of type roles, spacing, colors, surfaces, and component treatments. Define reusable tokens as needed; avoid scattered arbitrary values or a speculative full design system.
* Match density to the task: frequent comparison benefits from compact aligned information; exploration or storytelling may need more space and imagery. Preserve comfortable reading and interaction in either case.
* Use brand expression where it strengthens identity without competing with essential information. No font, palette, radius, or decorative style is a universal default.

## Layout and Visual Hierarchy

* Establish clear action priority and information order for the current task; use grouping and a reading path appropriate to content and locale.
* Keep labels, help, controls, and actions near what they affect. Distinguish primary, secondary, and destructive actions.
* Use whitespace to separate groups while keeping related content close. Avoid equal emphasis, universal centering, cramped or excessive spacing, and heroes that bury useful content.
* Choose structure for the task: tables for comparison, lists for scanning, cards for distinct items with meaningful summaries, and split views for selection plus detail. Use sidebars for persistent navigation when warranted; avoid panels with no grouping purpose.
* Prioritize overview, meaningful changes, and actionable detail in dashboards. In marketing pages, establish the offer and useful next action early, then supporting evidence; add sections only when content warrants them.

## Typography

* Use consistent roles for headings, body, labels, help, and metadata. Keep size, line length, and line height readable; communicate hierarchy beyond color.
* Avoid oversized headings, excessive weights, centered long text, low contrast, and uppercase blocks that impair reading or conflict with product identity.
* Test long headings, localized labels, and missing values. Wrap naturally; truncate only with a usable way to access the full content. Align comparable numbers and show units consistently.

## Spacing and Alignment

* Use the established spacing scale, consistent padding, shared alignment lines, container widths, and page gutters. Keep within-group gaps smaller than between-group gaps.
* Fix alignment and spacing directly instead of adding compensating wrappers.

## Color, Borders, Radius, and Effects

* Use theme tokens with sufficient contrast; use color for hierarchy, status, or brand.
* Keep borders, radii, accents, shadows, and effects consistent and restrained.
* Never let decorative effects or translucency reduce readability.

## Components and Content

* Keep density appropriate, labels clear, copy concise, and icons informative and consistent. Use emojis only when intentional to the product; label unfamiliar icon actions.
* Never present placeholders, metrics, testimonials, activity, or social proof as real without evidence.
* Design with realistic, non-sensitive content lengths and quantities. Clearly label demonstration data; preserve missing, zero, empty, and unknown business values as distinct states.
* Use action labels that describe the outcome. Empty states should explain the situation and a useful next step; distinguish no records from no filter matches or failed loading.

## Forms and Data-Dense Interfaces

* Use visible labels, required/optional cues, logical grouping, and nearby actionable errors; placeholders do not replace labels.
* Ask only for necessary information not already known or safely derivable. Use accurate, editable defaults and controls suited to input, frequency, and precision; preserve paste and autofill.
* Validate at useful moments, such as blur or submission, without interrupting unfinished input. Associate errors with fields, explain how to fix them, and preserve input after recoverable failures. Client validation aids usability; server validation enforces rules.
* Keep submission progress and outcome clear; prevent accidental duplicates without leaving controls permanently disabled after failure. Preserve existing Enter-key submission and keyboard behavior.
* Make tables readable and responsive. Keep comparison columns aligned; expose active filters and a clear reset. Preserve relevant selection and filter state across supported navigation. Bulk actions must show their scope; pagination or virtualization should fit the dataset and existing behavior.
* Keep data and actions legible; charts need meaningful labels, units, and comparisons without misleading scales or decorative clutter.

## Interaction States

* Handle relevant default, hover, focus, active, selected, disabled, loading, success, empty, and error states. Acknowledge processing, outcome, and next steps without redundant indicators for instant work.
* Keep layout stable during loading; use skeletons only where the structure is predictable. Distinguish initial loading, refreshing, and submitting when their effects differ; keep unaffected actions usable.
* Prevent accidental duplicates; explain disabled actions and consequences when unclear. Offer retry for recoverable failures without losing work. Prefer undo when feasible; confirm consequential mistakes with a clear action and consequence.

## Responsive Design

* Preserve information and action priority on small screens through deliberate stacking, wrapping, collapsing, or scrolling; do not simply shrink desktop layouts or hide essential actions.
* Keep text readable, controls touch-friendly, and reading/action/keyboard order logical. Check narrow, medium, and wide layouts when tools allow, including long content and zoom; avoid accidental overflow.
* Choose breakpoints where content stops working. Adapt navigation and dense tables deliberately; retain labels, comparison context, and access to actions. Restrict horizontal scrolling to content that needs it.

## Accessibility

* Use semantic HTML, keyboard-operable controls, visible unobscured focus, and usable target sizes. Provide accessible names and label/help/error associations.
* Preserve heading, reading, and focus order, including dialogs and dynamic views; announce meaningful status changes appropriately.
* Maintain contrast and non-color state cues. Use ARIA only when native semantics are insufficient; respect reduced motion. Verify applicable accessibility requirements, not appearance alone.
* Use links for navigation and buttons for actions. Test keyboard-only completion; menus and dialogs need appropriate focus entry, dismissal, and return. Modal dialogs must contain focus while open without creating a keyboard trap.
* Provide useful alternative text for meaningful imagery and hide decorative imagery from assistive technology. Hover-only information must also be available through focus or another accessible interaction.

## Motion and Feedback

* Use motion to clarify state, hierarchy, or continuity; avoid distracting, blanket, or slow animation.
* Give immediate feedback through the least disruptive pattern.
* Put control-specific validation inline. Use toasts only for brief non-blocking status and modals only for required decisions, consequential confirmation, or acknowledgement.
* Never put information requiring action only in a disappearing toast, interrupt routine actions with a modal, or add redundant success feedback.

## AI-Slop Prevention

* Every container, effect, badge, illustration, and text block should support product identity, hierarchy, comprehension, interaction, or feedback. Improve weak structure before adding decoration.
* Check for repeated card grids where aligned rows aid comparison, nested panels without meaningful grouping, competing accents, excessive empty space, and copy that repeats headings without adding information.
* Cards, gradients, large headings, rounded corners, and animation are valid when purposeful. Choose them deliberately for the product; do not assemble the same hero, feature grid, and dashboard treatment for every task.

## Final Design Review

* Review the affected task flow with realistic content and relevant success, empty, loading, disabled, and failure states. Check discoverability, hierarchy, effort, recovery, and visual consistency.
* Use available local browser/tools to inspect narrow and wide layouts and complete affected actions with pointer and keyboard. Check long content, zoom, focus, and overflow where relevant. Screenshots support visual review but cannot prove interaction or accessibility.
* For visual changes, compare affected behavior before and after: submission, validation, navigation, state transitions, API integration, and permission-dependent controls as applicable. Run meaningful existing checks for regression risks; do not add tests that merely mirror styling.
* Correct unmet requirements. Report observed results, checks not run, and remaining risks; distinguish static review from browser verification. If tools or a local environment are unavailable, disclose the limit instead of claiming the flow works. Stop when the task and required verification are complete.
