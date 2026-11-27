# Claude Dev Agents

**A modular, open-source agent ecosystem for Claude Code across the software development lifecycle.**

Claude Dev Agents helps developers assemble an AI engineering team from independently installable components: a shared Core, domain teams, technology specialists, and optional skills.

> **Project status:** early preview. Core and Frontend plugins, plus three optional first-party skill plugins, are available for testing. The integration workflow and cost policy are being refined; this is not yet a stable production release.

## Project vision

Build a practical engineering system for Claude Code that helps developers plan, implement, review, test, secure, and ship software with clear responsibilities and evidence-based quality control.

The project is **Claude Code-only**. It uses Claude Code's native agents, skills, commands, hooks, and plugin marketplace rather than creating a separate agent runtime.

## Install only in projects where you want it

First, register the marketplace catalogue once:

```powershell
claude plugin marketplace add AVL05/claude-dev-agents
```

This registers the catalogue in your Claude Code user settings. It does **not** enable or load the marketplace's agents in every project. Only enabled plugins add components and context to a session.

From the root of the project where you want Claude Dev Agents, install with **local scope**:

```powershell
claude plugin install cda-core@claude-dev-agents --scope local
claude plugin install cda-frontend@claude-dev-agents --scope local
```

Install only the optional skills you want, also with local scope:

```powershell
claude plugin install cda-frontend-quality@claude-dev-agents --scope local
claude plugin install cda-design-review@claude-dev-agents --scope local
claude plugin install cda-accessibility-review@claude-dev-agents --scope local
```

### Scope choices

| Scope | Who gets the plugin | Recommended use |
| --- | --- | --- |
| `local` | You, in this repository only | **Default.** Personal opt-in per project |
| `project` | Everyone working in this repository, through committed project settings | Teams that intentionally share the setup |
| `user` | You, in every project on this machine | Not the default for this project |

To remove a plugin from the current local project:

```powershell
claude plugin uninstall cda-frontend@claude-dev-agents --scope local
```

The marketplace catalogue can remain registered without enabling any plugin. Remove the catalogue itself only if you no longer want it available in Claude Code.

## Cost-aware by design

An enabled plugin contributes its component names and descriptions to Claude's context on every turn. Full agent and skill instructions load when invoked. Use `claude plugin details <plugin>@claude-dev-agents` to inspect the estimated always-on and on-invoke footprint.

Claude Dev Agents therefore follows these defaults:

- Install plugins only in projects that need them.
- Keep agent descriptions short and specific.
- Do not spawn agents for trivial work.
- Use one implementer by default for a normal feature.
- Delegate planning **or** architecture, not both, unless complexity justifies it.
- Run one targeted review pass by default; repeat only after blocker/major fixes.
- Prefer project tests and direct diff inspection over redundant reviewer calls.
- Keep parallelism at two by default; use three only for independent work.
- Keep agent reports concise and evidence-based.

See [the cost and efficiency policy](docs/cost-efficiency.md).

## Modular by design

Users should install only what they need:

| Layer | Purpose | Examples |
| --- | --- | --- |
| **Core** | Shared orchestration and baseline engineering capabilities | Engineering Director, general engineering |
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

Quality control is risk-based. It does not launch every reviewer on every change.

## Hybrid autonomy

Routine, reversible work can proceed autonomously within the user's request. The system must seek approval before high-impact actions such as destructive operations, major architectural changes, new dependencies with meaningful risk, database migrations, production changes, publishing, or deployment.

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
- [Cost and efficiency policy](docs/cost-efficiency.md)
- [Optional skill integrations](docs/skill-integration.md)
- [Hybrid autonomy and safety](docs/autonomy-and-safety.md)
- [Evaluation strategy](docs/evaluation-strategy.md)
- [Roadmap](docs/roadmap.md)
- [Frontend quality standards](docs/quality-standards.md)
- [Contributing](CONTRIBUTING.md)

## Local validation

From the repository root:

```powershell
claude plugin validate .
claude plugin validate .\plugins\core
claude plugin validate .\plugins\teams\frontend
```

Then test a real installation in a clean Claude Code profile. See the [official plugin creation documentation](https://code.claude.com/docs/en/plugins/create) and [marketplace documentation](https://code.claude.com/docs/en/plugins/create-marketplace).

## License

MIT. See [LICENSE](LICENSE).
