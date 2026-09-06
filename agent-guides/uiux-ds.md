<!-- UI/UX standards for consistent, accessible, responsive, and purposeful interfaces. -->

# UI/UX Design Standards

## Section Routing

* **New screen or redesign:** Read all sections below, adding forms and motion only when relevant.
* **Existing component styling:** [Existing Design System First](#existing-design-system-first), [Spacing and Alignment](#spacing-and-alignment), [Color, Borders, Radius, and Effects](#color-borders-radius-and-effects), [Interaction States](#interaction-states), [Accessibility](#accessibility), and [Final Design Review](#final-design-review); add typography or responsive guidance when affected.
* **Forms, tables, dashboards, or data-dense UI:** [Existing Design System First](#existing-design-system-first), [Forms and Data-Dense Interfaces](#forms-and-data-dense-interfaces), [Interaction States](#interaction-states), [Responsive Design](#responsive-design), [Accessibility](#accessibility), and [Final Design Review](#final-design-review).
* **Responsive or accessibility fix:** The directly relevant [Responsive Design](#responsive-design), [Accessibility](#accessibility), and affected [Interaction States](#interaction-states), then [Final Design Review](#final-design-review).
* **Animation or feedback:** [Interaction States](#interaction-states), [Motion and Feedback](#motion-and-feedback), [Accessibility](#accessibility), and [Final Design Review](#final-design-review).
* **Marketing or template-risk review:** [Understand the Product Before Designing](#understand-the-product-before-designing), [Components and Content](#components-and-content), [AI-Slop Prevention](#ai-slop-prevention), and [Final Design Review](#final-design-review).

## Understand the Product Before Designing

* Start from the actual product, audience, task, context, and likely errors. Make needed information and the next action discoverable; minimize unnecessary decisions and effort without hiding consequences.
* Match familiar product flows and language. Use recognition over recall; reveal secondary detail when needed without hiding essential controls. Adapt to user experience only where justified.
* Treat psychology as contextual hypotheses, not guaranteed conversion tactics. Preserve informed choices, honest progress, and easy refusal or cancellation; never use deception or obstructive defaults.
* These are design defaults, not a visual style. Deviate for a clear product, brand, accessibility, or usability reason; in new projects, add only foundations needed now.

## Existing Design System First

* Inspect surrounding screens, branding, components, installed libraries, tokens, and interaction patterns before styling.
* Prefer project components, then suitable installed libraries, existing tokens/variants, and composition or extension; use custom UI only when these are unsuitable. Reuse accessible state and keyboard behavior without forcing awkward UX.
* Do not install or replace a UI library without permission. Keep styling within the existing system.

## Layout and Visual Hierarchy

* Establish clear action priority and information order for the current task; use grouping and a reading path appropriate to content and locale.
* Keep labels, help, controls, and actions near what they affect. Distinguish primary, secondary, and destructive actions.
* Use whitespace to separate groups while keeping related content close. Avoid equal emphasis, universal centering, cramped or excessive spacing, and heroes that bury useful content.

## Typography

* Use consistent roles for headings, body, labels, help, and metadata. Keep size, line length, and line height readable; communicate hierarchy beyond color.
* Avoid oversized headings, excessive weights, centered long text, low contrast, and uppercase blocks that impair reading or conflict with product identity.

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

## Forms and Data-Dense Interfaces

* Use visible labels, required/optional cues, logical grouping, and nearby actionable errors; placeholders do not replace labels.
* Ask only for necessary information not already known or safely derivable. Use accurate, editable defaults and controls suited to input, frequency, and precision; preserve paste and autofill.
* Validate contextually and preserve input after recoverable failures. Client validation aids usability; server validation enforces rules.
* Make tables readable and responsive. Provide useful empty states and clear search, filter, pagination, and bulk actions when relevant.
* Keep data and actions legible; charts need meaningful labels, units, and comparisons without misleading scales or decorative clutter.

## Interaction States

Handle relevant default, hover, focus, active, selected, disabled, loading, success, empty, and error states. Acknowledge actions and communicate processing, outcome, and next steps without redundant indicators for instant work. Prevent accidental duplicates; explain disabled actions and consequences when unclear. Prefer recoverable actions or undo when feasible; use confirmation for consequential mistakes.

## Responsive Design

* Preserve information and action priority on small screens through deliberate stacking, wrapping, collapsing, or scrolling; do not simply shrink desktop layouts or hide essential actions.
* Keep text readable, controls touch-friendly, and reading/action/keyboard order logical. Check narrow, medium, and wide layouts when tools allow, including long content and zoom; avoid accidental overflow.

## Accessibility

* Use semantic HTML, keyboard-operable controls, visible unobscured focus, and usable target sizes. Provide accessible names and label/help/error associations.
* Preserve heading, reading, and focus order, including dialogs and dynamic views; announce meaningful status changes appropriately.
* Maintain contrast and non-color state cues. Use ARIA only when native semantics are insufficient; respect reduced motion. Verify applicable accessibility requirements, not appearance alone.

## Motion and Feedback

* Use motion to clarify state, hierarchy, or continuity; avoid distracting, blanket, or slow animation.
* Give immediate feedback through the least disruptive pattern.
* Put control-specific validation inline. Use toasts only for brief non-blocking status and modals only for required decisions, consequential confirmation, or acknowledgement.
* Never put information requiring action only in a disappearing toast, interrupt routine actions with a modal, or add redundant success feedback.

## AI-Slop Prevention

Every container, effect, badge, illustration, and text block should support product identity, hierarchy, comprehension, interaction, or feedback. Avoid template-driven heroes, repeated card grids, nested panels, competing accents, gradients/glows, excessive empty space, and redundant copy without that purpose. Choose dashboards, cards, inline editing, or dialogs for the task; none is a universal default. Improve weak structure instead of adding decoration.

## Final Design Review

Review the affected task flow with realistic content and relevant success, empty, loading, and failure states. Check discoverability, effort, recovery, visual consistency, responsive behavior, keyboard/focus access, and accessibility. Use available local browser/tools to verify interaction; a screenshot alone cannot prove usability. Correct unmet requirements, report unverified behavior, and stop when the task is satisfied.
