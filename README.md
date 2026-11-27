# Claude Dev Agents

**A modular, open-source agent ecosystem for Claude Code across the software development lifecycle.**

Claude Dev Agents is designed for developers who want to assemble a capable AI engineering team from independently installable components: a shared core, domain teams, technology specialists, and optional skills.

> **Project status:** early development. The repository currently contains an initial frontend agent prototype and its standards. The modular plugin marketplace, additional teams, installation flows, and evaluation suite are planned work—not yet a released product.

## Project vision

Build a practical engineering system for Claude Code that helps developers plan, implement, review, test, secure, and ship software with clear responsibilities and evidence-based quality control.

The project is **Claude Code-only**. It uses Claude Code's native agents, skills, commands, hooks, and plugin marketplace capabilities rather than creating a separate agent runtime.

## Modular by design

Users should install only what they need:

| Layer | Purpose | Examples |
| --- | --- | --- |
| **Core** | Shared orchestration and engineering standards | Engineering Director, project planning, architecture |
| **Domain teams** | Specialists for areas of software delivery | Frontend, backend, database, QA, security, DevOps, AI engineering |
| **Technology packs** | Guidance for a concrete language or framework | React/Next.js, Vue/Nuxt, Angular, Svelte, Laravel/PHP, Python/FastAPI |
| **Skills** | Optional methods and focused workflows | Design direction, testing strategy, accessibility, API design |

A full-stack setup is a combination of the teams required by a project—not a separate monolithic package with duplicated agents.

### Optional skills stay optional

- Users choose which skills to install and invoke.
- Third-party skills remain distributed and maintained by their original authors.
- We do not copy, bundle, or silently install external skills.
- [Premium Frontend Director](https://github.com/AVL05/premium-frontend-director) remains an independent project and can be installed separately.
- Agent definitions must remain useful without any optional companion skill.

## Three-level operating model

1. **Director:** understands the request, selects available specialists, plans delegation, and owns the final result.
2. **Specialists:** perform bounded work in their area of expertise.
3. **Quality control:** checks acceptance criteria, tests, security, and evidence before delivery.

Quality control is a cross-cutting responsibility. It should activate the checks relevant to the task, not launch every reviewer on every change.

## Hybrid autonomy

Routine, reversible work can proceed autonomously within the user's request. The system must seek approval before high-impact actions such as destructive operations, major architectural changes, new dependencies with meaningful risk, database migrations, production changes, publishing, or deployment.

## Engineering principles

- Inspect the repository and its instructions before making changes.
- Use only specialists that are available and relevant to the task.
- Do not invent agents, skills, tools, scripts, test results, or performance metrics.
- Keep responsibilities narrow and avoid overlapping edits.
- Prefer the smallest coherent implementation over unnecessary rewrites.
- Measure quality; do not rely on confident agent self-assessment.
- Keep the user in control of consequential actions.
- Make the system useful without mandatory external APIs or paid companion skills.

## AI engineering, not prompt collection

The project's value must come from reliable engineering workflows—not from the number of Markdown agent files. We intend to evaluate agent-assisted work against a plain Claude Code baseline using reproducible tasks, automated checks, review rubrics, and transparent limitations.

See [the evaluation strategy](docs/evaluation-strategy.md).

## Repository documentation

- [Product vision](docs/product-vision.md)
- [Modular architecture](docs/architecture.md)
- [Optional skill integrations](docs/skill-integration.md)
- [Hybrid autonomy and safety](docs/autonomy-and-safety.md)
- [Evaluation strategy](docs/evaluation-strategy.md)
- [Roadmap](docs/roadmap.md)
- [Frontend quality standards](docs/quality-standards.md)
- [Contributing](CONTRIBUTING.md)

## Development status

The current `.claude/agents/` resources are an early frontend prototype. They are useful for developing and evaluating the first team, but the public marketplace packaging and final installation commands are not ready yet. We will publish installation instructions only after validating the native plugin structure and clean-install experience.

## License

MIT. See [LICENSE](LICENSE).
