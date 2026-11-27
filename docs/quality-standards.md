# Frontend Quality Standards

These are shared review criteria, not a claim that every project uses the same stack.

## Functional correctness

- Identify expected behavior and affected user journeys before editing.
- Cover loading, empty, success, error, and disabled states where relevant.
- Preserve existing routes, data contracts, and interaction patterns unless change is requested.
- Handle asynchronous work, cancellation, and duplicate submissions deliberately.

## Visual quality

- Establish hierarchy through typography, spacing, alignment, and contrast.
- Use consistent design tokens and existing components before adding new ones.
- Avoid generic hero-plus-gradient layouts when they do not serve the product.
- Check narrow mobile, tablet, and desktop layouts.
- Inspect hover, focus, active, selected, loading, and validation states.
- Avoid arbitrary decoration that weakens clarity or content priority.

## Accessibility

- Prefer semantic HTML and native controls.
- Ensure all functionality is keyboard operable.
- Provide visible focus indicators and meaningful accessible names.
- Associate form labels and errors with their controls.
- Do not communicate status through color alone.
- Respect reduced-motion preferences.
- Check contrast against WCAG 2.2 AA criteria; automated checks do not replace manual review.

## Performance

- Measure before optimizing and record the measurement method.
- Avoid unnecessary client-side JavaScript and duplicated state.
- Optimize images and fonts appropriate to the project.
- Watch layout shifts, long tasks, and expensive repeated rendering.
- Do not claim a performance improvement without comparable evidence.

## Engineering hygiene

- Follow existing linting, formatting, typing, and test conventions.
- Keep components cohesive and avoid premature abstraction.
- Add or update tests for meaningful behavior changes.
- Do not suppress errors or weaken checks merely to obtain a green build.
- Report exact commands and outcomes.
