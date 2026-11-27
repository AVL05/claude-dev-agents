---
name: design-review
description: Run a structured visual and interaction review of a frontend screen or feature. Use after implementation or when a UI needs a quality assessment.
---

# Design Review Workflow

1. Identify the target route, audience, primary task, and success action.
2. Inspect the rendered interface at representative mobile, tablet, and desktop widths when tooling is available.
3. Review hierarchy, spacing, typography, alignment, color, content density, and consistency.
4. Exercise primary interactions and inspect focus, hover, active, disabled, loading, empty, and error states.
5. Record concrete defects before proposing subjective refinements.
6. Rank findings by severity and user impact.
7. Recheck each correction against the same viewport and state.

## Output format

- **Blockers:** issues that prevent task completion or create serious usability problems.
- **High priority:** major hierarchy, responsive, or interaction defects.
- **Polish:** lower-impact refinements.
- **Not verified:** states or devices that could not be inspected.

Never state that visual QA is complete if the interface was not rendered or inspected.
