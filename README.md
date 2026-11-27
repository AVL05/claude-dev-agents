# Claude Dev Agents

A focused, quality-first toolkit of specialized agents, skills, and workflows for Claude Code. The initial release targets **production-grade frontend engineering**: architecture, implementation, visual review, accessibility, and performance.

> Status: early development. The project is intentionally starting with a small, opinionated frontend team rather than a large collection of generic agents.

## What this project is

Claude Dev Agents is a reusable repository of Claude Code resources:

- **Agents** — focused specialists with explicit responsibilities and deliverables.
- **Skills** — reusable workflows and standards loaded when relevant.
- **Commands** — repeatable entry points for common engineering tasks.
- **Quality gates** — review checklists and CI validation to reduce regressions.

It is designed to work with existing projects, not replace their frameworks, tooling, or conventions.

## Initial specialist team

| Specialist | Responsibility |
| --- | --- |
| `frontend-director` | Coordinates specialists, scopes work, and owns final delivery. |
| `frontend-architect` | Understand the codebase, define boundaries, and plan maintainable frontend changes. |
| `frontend-implementer` | Implement polished, responsive, production-ready interfaces. |
| `design-reviewer` | Review visual hierarchy, layout, interaction, and design consistency. |
| `accessibility-auditor` | Audit semantics, keyboard access, focus, forms, and WCAG risks. |
| `performance-auditor` | Identify measurable frontend performance issues and prioritize fixes. |

Specialists should be invoked when their expertise is useful; do not force every agent into every task.

## Three-level architecture

1. **Director:** `frontend-director` coordinates substantial frontend work.
2. **Specialists:** architect, implementer, design reviewer, accessibility auditor, and performance auditor handle bounded tasks.
3. **Quality control:** the director selects relevant reviews, verifies project checks, and reports unresolved risks.

The director delegates selectively. Small tasks should use fewer agents; independent tasks may run in parallel, while dependent or overlapping edits should be sequenced.

## Repository layout

```text
.claude/
  agents/             # Specialist agent definitions
  commands/           # Explicit repeatable workflows
  skills/             # Reusable domain workflows
docs/
  architecture.md
  quality-standards.md
.github/workflows/
  validate.yml
```

## Installation

Copy the `.claude/` directory into the root of your project, or clone this repository and selectively copy the resources you need.

Claude Code discovers project-level agents, commands, and skills from the `.claude/` directory. Review each resource and adapt it to the target repository before use.

## Recommended workflow

1. Ask the architect to inspect the existing stack and propose a minimal implementation plan.
2. Implement in small, reviewable increments.
3. Run the design reviewer against the actual changed screens and states.
4. Run accessibility and performance audits where applicable.
5. Execute the project's own lint, type-check, tests, and build commands.
6. Review the final diff; never treat an agent's report as proof that a command passed.

## Design principles

- **Inspect before changing.** Respect existing architecture, dependencies, naming, and conventions.
- **Evidence over assumptions.** Distinguish inspected facts, hypotheses, and unverified claims.
- **No needless rewrites.** Prefer the smallest coherent change.
- **Quality is functional and visual.** A polished screenshot is not enough if keyboard, responsive, loading, or error states fail.
- **Accessible by default.** Semantic HTML, visible focus, sufficient contrast, and reduced-motion support are baseline expectations.
- **Measure before optimizing.** Avoid speculative performance changes.
- **Honest reporting.** State exactly which checks ran, which passed, and which remain unverified.

## Compatibility

The resources are Markdown-based and intended for Claude Code. Individual features may depend on the Claude Code version and project configuration. Keep project-specific commands and tool permissions under the user's control.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) and [docs/quality-standards.md](docs/quality-standards.md).

## License

MIT. See [LICENSE](LICENSE).
