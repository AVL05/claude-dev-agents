---
name: frontend-quality
description: Apply a consistent production-quality checklist when implementing or reviewing frontend work. Use when a task changes user-facing UI, interactions, forms, or responsive behavior.
---

# Frontend Quality Workflow

Use this skill as a practical checklist, adapting it to the actual project.

## Before implementation

- Read repository instructions and inspect nearby code.
- Identify the user goal, affected route, and expected behavior.
- Confirm existing components, tokens, breakpoints, and conventions.
- List relevant states: initial, loading, success, empty, error, disabled, and validation.

## During implementation

- Prefer semantic HTML and existing components.
- Keep responsive behavior intentional rather than shrinking desktop layouts.
- Make interactive elements genuinely functional.
- Provide keyboard access, visible focus, and accessible names.
- Avoid unnecessary dependencies and client-side JavaScript.

## Before completion

- Review mobile, tablet, and desktop behavior.
- Check interaction and error states.
- Run the project's relevant lint, type-check, tests, and build scripts when available.
- Inspect the final diff.
- Report checks accurately, including anything not tested.
