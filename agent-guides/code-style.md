# Code Style and Formatting

## Readability

* Organize new code into clear sections so a reader can quickly identify related parts, such as imports, types, constants, state, event handlers, rendering, and helper functions.
* Use consistent indentation and spacing. Follow the project’s established conventions when they are clear, readable, and maintainable; do not preserve a convention merely because it already exists if it produces unnecessarily difficult-to-read code.
* Keep imports, declarations, state, handlers, markup, helper functions, and related sections logically organized.
* Prefer one logical operation or declaration per line when combining them would reduce readability.
* Use line breaks and grouping to keep long expressions, function calls, object literals, and JSX readable.
* Prefer clear names and straightforward control flow over compressed or clever code.

## Scope of Formatting

* New code must follow these readability and formatting rules as it is written.
* When modifying an existing code block, improve formatting within that changed block when needed to keep the resulting code readable.
* Do not reformat untouched code, entire files, or unrelated sections merely to make them match this style.
* Do not run whole-file formatting or make formatting-only refactors outside the requested scope.

## Project Conventions

* Follow the project’s existing formatter configuration, indentation style, naming conventions, and component patterns when they are available.
* If an existing convention is clearly poor, use a consistent, conventional, and readable style for new code and for the code blocks being modified.
* Do not impose tabs, spaces, line widths, or other formatting preferences on unrelated existing code solely to make the whole project uniform.
* If no project convention exists, choose a consistent, conventional, and readable style for the new code.

## Review Standard

Before finishing, check that changed code is properly indented, readable without reformatting, and free of avoidable compressed structures or unrelated formatting changes.
