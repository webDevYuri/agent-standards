<!-- UI/UX standards for consistent, accessible, responsive, and purposeful interfaces. -->

# UI/UX Design Standards

## Section Routing

* **New screen or redesign:** [Understand the Product Before Designing](#understand-the-product-before-designing), [Existing Design System First](#existing-design-system-first), [Layout and Visual Hierarchy](#layout-and-visual-hierarchy), [Typography](#typography), [Spacing and Alignment](#spacing-and-alignment), [Color, Borders, Radius, and Effects](#color-borders-radius-and-effects), [Components and Content](#components-and-content), [Interaction States](#interaction-states), [Responsive Design](#responsive-design), [Accessibility](#accessibility), [AI-Slop Prevention](#ai-slop-prevention), and [Final Design Review](#final-design-review). Add forms or motion sections only when relevant.
* **Existing component styling:** [Existing Design System First](#existing-design-system-first), [Spacing and Alignment](#spacing-and-alignment), [Color, Borders, Radius, and Effects](#color-borders-radius-and-effects), [Interaction States](#interaction-states), and [Final Design Review](#final-design-review); add responsive guidance when affected.
* **Forms, tables, dashboards, or data-dense UI:** [Existing Design System First](#existing-design-system-first), [Forms and Data-Dense Interfaces](#forms-and-data-dense-interfaces), [Interaction States](#interaction-states), [Responsive Design](#responsive-design), [Accessibility](#accessibility), and [Final Design Review](#final-design-review).
* **Responsive or accessibility fix:** The directly relevant [Responsive Design](#responsive-design), [Accessibility](#accessibility), and affected [Interaction States](#interaction-states), then [Final Design Review](#final-design-review).
* **Animation or feedback:** [Interaction States](#interaction-states), [Motion and Feedback](#motion-and-feedback), [Accessibility](#accessibility), and [Final Design Review](#final-design-review).
* **Marketing or template-risk review:** [Understand the Product Before Designing](#understand-the-product-before-designing), [Components and Content](#components-and-content), [AI-Slop Prevention](#ai-slop-prevention), and [Final Design Review](#final-design-review).

## Understand the Product Before Designing

* Design for the product, audience, screen purpose, and primary task—not decorative novelty or a trend showcase.
* Inspect surrounding screens, branding, design language, components, installed libraries, typography, spacing and color tokens, and interaction patterns.
* Match established patterns; do not make an isolated screen feel unrelated. In a new project, derive direction from the brief and add only foundations needed now.
* Treat these as firm defaults; deviate only for a clear brand, requirement, design-system, or usability reason.

## Existing Design System First

Use this priority order:

1. Existing project-specific components.
2. Installed libraries such as shadcn/ui, DaisyUI, Radix-based systems, internal libraries, or framework UI systems.
3. Existing tokens, variants, and utility classes.
4. Composition or extension of existing components.
5. Custom UI only when existing options are genuinely unavailable or unsuitable.

* Prefer components that already handle accessibility, states, keyboard behavior, and responsiveness, but do not force awkward use that harms UX.
* Do not recreate common buttons, dialogs, dropdowns, inputs, tabs, tables, tooltips, sheets, or alerts when a suitable component exists.
* Do not install or replace a UI library without permission.
* Keep styling within the design system; avoid arbitrary colors, fonts, spacing, icons, and components.

## Layout and Visual Hierarchy

* Establish one clear primary action or focal point, intentional content order, obvious grouping, and a natural reading path based on the information architecture.
* Keep labels, help, controls, and actions near what they affect. Distinguish primary, secondary, and destructive actions.
* Use consistent alignment and purposeful whitespace.
* Avoid universal centering, equal emphasis, excessive emptiness, cramped density, oversized heroes that bury useful content, or decoration that weakens usability.

## Typography

* Use a small, consistent set of roles for headings, labels, body, support text, and metadata.
* Keep line length, size, and line height readable; communicate hierarchy through typography, not color alone.
* Avoid generic oversized headings, excessive weights or sizes, centered long-form text, low contrast, uppercase blocks, and typography that conflicts with product identity.

## Spacing and Alignment

* Use the established spacing scale: consistent gaps within groups, larger separation between groups, and deliberate vertical rhythm.
* Share alignment lines, container widths, and page gutters across related content.
* Avoid arbitrary values, small label/icon/field/button misalignments, inconsistent component padding, and wrappers that compensate for poor spacing.

## Color, Borders, Radius, and Effects

* Use theme tokens with sufficient contrast; use color for hierarchy, status, or brand.
* Keep borders, radii, accents, shadows, and effects consistent and restrained.
* Never let decorative effects or translucency reduce readability.

## Components and Content

* Build components for real product needs and reuse patterns for repeated behavior.
* Keep density appropriate, labels clear, copy concise, and icon size and placement consistent.
* Use icons only when informative and emojis only when the product intentionally does so.
* Never present placeholders or invented content as real product data.

## Forms and Data-Dense Interfaces

* Use visible labels, clear required or optional states, logical grouping, appropriate controls, and nearby actionable validation; never rely on placeholders as labels.
* Keep forms concise and errors specific.
* Make tables readable and responsive. Provide useful empty states and clear search, filter, pagination, and bulk actions when relevant.
* Do not hide important actions behind unclear icons or let decorative dashboards obscure data.

## Interaction States

Handle every relevant default, hover, focus, active, selected, disabled, loading, success, empty, and error state. Prevent duplicate actions while loading when appropriate. Errors must explain what happened and what to do next.

## Responsive Design

* Design small screens intentionally; preserve action priority instead of shrinking desktop layouts or hiding essential actions.
* Use appropriate stacking, wrapping, collapsing, and intentional scrolling with touch-friendly controls, readable text, and usable forms.
* Preserve logical reading, action, and keyboard order across rearrangement; avoid accidental overflow and excessively tall spacing.
* When tools are available, review narrow, medium, and wide layouts rather than trusting breakpoints alone.

## Accessibility

* Use semantic HTML and keyboard-operable controls with visible focus.
* Provide correct accessible names and associations among labels, descriptions, and errors.
* Preserve heading, reading, and focus order, including dialogs and dynamic views.
* Maintain contrast and non-color state indicators. Use ARIA only when native semantics are insufficient and support reduced motion when motion is substantial.

## Motion and Feedback

* Use restrained motion only to explain state, hierarchy, or continuity; avoid blanket load animation, excessive hover movement, slow transitions, and distraction.
* Give immediate feedback through the least disruptive pattern.
* Put control-specific validation inline. Use toasts only for brief non-blocking status and modals only for required decisions, consequential confirmation, or acknowledgement.
* Never put information requiring action only in a disappearing toast, interrupt routine actions with a modal, or add redundant success feedback.

## AI-Slop Prevention

Do not default to generic SaaS heroes; oversized or gradient headlines; eyebrow pills above every heading; repeated three-card grids; excessive rounded cards; random glass panels, gradients, glows, blobs, patterns, or translucent surfaces; fake metrics, testimonials, activity, social proof, or logo rows; meaningless or excessive icons; decorative badges; generic startup copy; identical section treatment; copied landing templates; or unbranded dark purple/blue glowing themes.

Use any such pattern only for a specific product, brand, content, or usability reason. The result must look designed for this product, not generated from a template.

## Final Design Review

Before completion, confirm:

* The primary action is clear and the interface matches the product.
* Existing components and libraries were reused; no custom UI is unnecessary.
* Hierarchy, spacing, typography, borders, radii, shadows, and effects are consistent and purposeful.
* Relevant states, mobile usability, keyboard access, focus, and accessibility are complete.
* No section feels generic, repetitive, template-like, or obviously AI-generated.
* The result is production-ready, not merely impressive in a screenshot.

Revise weak sections instead of adding decoration.
