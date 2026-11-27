# Claude Dev Agents

**A modular, open-source agent ecosystem for Claude Code across the software development lifecycle.**

Claude Dev Agents helps developers assemble an AI engineering team from independently installable components: a shared Core, domain teams, technology specialists, and optional skills.

> **Project status:** early preview. The first Core and Frontend plugin packages and three optional first-party skill plugins are present. Claude Code CLI validation and clean-install testing are still pending before a stable release.

## Project vision

Build a practical engineering system for Claude Code that helps developers plan, implement, review, test, secure, and ship software with clear responsibilities and evidence-based quality control.

The project is **Claude Code-only**. It uses Claude Code's native agents, skills, commands, hooks, and plugin marketplace rather than creating a separate agent runtime.

## Install from the marketplace

Add the marketplace once:

```text
/plugin marketplace add AVL05/claude-dev-agents
```

Install the Core and only the teams you need:

```text
/plugin install cda-core@claude-dev-agents
/plugin install cda-frontend@claude-dev-agents
```

Optional first-party skill plugins can be installed independently:

```text
/plugin install cda-frontend-quality@claude-dev-agents
/plugin install cda-design-review@claude-dev-agents
/plugin install cda-accessibility-review@claude-dev-agents
```

These commands describe the current preview package names. Before a stable release, validate the marketplace locally with `claude plugin validate .` and complete a clean installation test in Claude Code. The GitHub Actions workflow validates marketplace JSON, plugin paths, names, and component frontmatter; it does not replace Claude Code's own validator or a real installation test.

## Modular by design

Users should install only what they need:

| Layer | Purpose | Examples |
| --- | --- | --- |
| **Core** | Shared orchestration and baseline engineering capabilities | Engineering Director, project planning, architecture, general engineering |
| **Domain teams** | Specialists for software disciplines | Frontend, backend, database, QA, security, DevOps, AI engineering |
| **Technology packs** | Guidance for a concrete language or framework | React/Next.js, Vue/Nuxt, Angular, Svelte, Laravel/PHP, Python/FastAPI |
| **Skills** | Optional methods and focused workflows | Design direction, testing strategy, accessibility, API design |

A full-stack setup is a combination of the teams required by a project—not a separate monolithic agent with duplicated responsibilities.

### Optional skills stay optional

- Users choose which skills to install and invoke.
- First-party skills from this marketplace are separate plugins.
- Third-party skills remain distributed and maintained by their original authors.
- We do not copy, bundle, or silently install external skills.
- [Premium Frontend Director](https://github.com/AVL05/premium-frontend-director) remains an independent project and can be installed separately.
- Agent definitions must remain useful without optional companion skills.

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

## Current plugins

| Plugin | Contents | Installation |
| --- | --- | --- |
| `cda-core` | Engineering Director, planner, architect, general engineer, reviewer | Recommended base |
| `cda-frontend` | Frontend architecture, implementation, design, accessibility, performance | Optional domain team |
| `cda-frontend-quality` | Frontend quality skill | Optional |
| `cda-design-review` | Visual review skill | Optional |
| `cda-accessibility-review` | Accessibility review skill | Optional |

Additional teams and technology packs will be added only after their responsibilities and workflows are validated.

## Documentation

- [Product vision](docs/product-vision.md)
- [Modular architecture](docs/architecture.md)
- [Optional skill integrations](docs/skill-integration.md)
- [Hybrid autonomy and safety](docs/autonomy-and-safety.md)
- [Evaluation strategy](docs/evaluation-strategy.md)
- [Roadmap](docs/roadmap.md)
- [Frontend quality standards](docs/quality-standards.md)
- [Contributing](CONTRIBUTING.md)

## Local validation

From the repository root:

```bash
claude plugin validate .
claude plugin validate ./plugins/core
claude plugin validate ./plugins/teams/frontend
```

Then test a real installation in a clean Claude Code profile. See the [official plugin creation documentation](https://code.claude.com/docs/en/plugins/create) and [marketplace documentation](https://code.claude.com/docs/en/plugins/create-marketplace).

## License

MIT. See [LICENSE](LICENSE).
