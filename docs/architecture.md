# Modular Architecture

## 1. Product scope

Claude Dev Agents targets the full software development lifecycle while remaining modular. It is built specifically for Claude Code and relies on Claude Code's native extension mechanisms.

The system is not a standalone agent runtime, hosted service, or framework generator. Claude Code remains the execution environment.

## 2. Distribution model

One public GitHub repository hosts one Claude Code marketplace. The marketplace exposes independently installable plugins grouped into four categories:

1. **Core plugin** — shared orchestration and baseline engineering capabilities.
2. **Domain team plugins** — specialists for software disciplines.
3. **Technology plugins** — framework/language-specific expertise.
4. **Skill plugins** — optional, focused workflows and methods.

The preview marketplace is defined in `.claude-plugin/marketplace.json`. Every listed plugin has its own `.claude-plugin/plugin.json` manifest and component directories at the plugin root.

## 3. Installation scope and opt-in behavior

Plugins must never be enabled globally by default.

- Recommended installation is `--scope local`, which enables the plugin for the current user in the current repository only and records it in `.claude/settings.local.json`.
- Use `--scope project` only when the repository owner intentionally wants to share the plugin activation with collaborators through committed `.claude/settings.json`.
- Use `--scope user` only when a user explicitly wants the plugin in every project on their machine.
- Registering the marketplace adds a catalogue source to user settings; it does not by itself enable the marketplace's plugins or add their agent descriptions to sessions.
- Users can uninstall or disable each plugin independently.

The install guide must always show local scope first. Never omit the scope flag from default installation commands.

## 4. Current package layout

```text
.claude-plugin/
  marketplace.json
plugins/
  core/
    .claude-plugin/plugin.json
    agents/
  teams/
    frontend/
      .claude-plugin/plugin.json
      agents/
  skills/
    frontend-quality/
    design-review/
    accessibility-review/
docs/
evaluations/
.github/workflows/
```

Future domain teams and technology packs will be added as independent plugin directories. The current `.claude/` files are retained as a development prototype until plugin installation has been validated; they are not the marketplace's canonical package paths.

## 5. Cost-aware execution

An enabled plugin contributes component names and descriptions to Claude's context on every turn. Full agent/skill instructions load when invoked. Therefore, installation scope and delegation policy are both product-level cost controls.

- Keep agent descriptions concise and action-specific.
- Keep optional skills in independent plugins.
- Avoid installing unused domain teams.
- Avoid redundant specialist roles and duplicate review work.
- Prefer direct execution for small changes.
- Use one implementer for ordinary feature work.
- Use a planner **or** architect for complex work, not both by default.
- Use one targeted review pass and one correction pass only for blocker/major findings or failed checks.
- Default to two concurrent agents; three only for independent tasks.
- Do not invoke an agent merely to repeat an existing test or summarize already-known context.

See [cost and efficiency policy](cost-efficiency.md).

## 6. Three-level operating model

### Level 1 — Director

The Core `engineering-director` is the primary entry point for cross-domain tasks. It translates requests into acceptance criteria, inspects repository instructions and the actual stack, selects installed specialists, sequences dependent work, and owns the final handoff. It can handle small changes and ordinary planning itself.

### Level 2 — Specialists

Specialists own bounded responsibilities and return concrete implementation or evidence. Planned teams include frontend, backend, database, quality, security, DevOps/platform, AI engineering, mobile, and data engineering.

### Level 3 — Quality control

Quality control is a cross-cutting gate coordinated by the Director. It selects relevant reviewers and objective checks based on risk. A report is not proof that a check passed: record commands run, results observed, and checks not run.

## 7. Technology specialists

The Core and domain teams should be technology-agnostic wherever possible. Technology packs add only the knowledge specific to a framework, runtime, or language.

Examples include React/Next.js, Vue/Nuxt, Angular, Svelte/Astro, Node.js/TypeScript, Laravel/PHP, and Python/FastAPI. Add a pack only when it has a distinct workflow, concrete examples, and evaluation cases.

## 8. Optional skill ecosystem

Skills are not mandatory dependencies of agent teams. First-party skills may be published as independent plugins in this marketplace. Third-party skills remain independent.

- Users decide which skills to install and invoke.
- Do not copy external skill files, scripts, assets, or documentation into this repository.
- Do not install or update a skill without user approval.
- Do not claim a skill was used unless it was actually available and invoked.
- Agents must retain a useful baseline workflow without optional skills.
- Avoid preloading every optional skill into every agent.

[Skill integration policy](skill-integration.md) documents the rules. [Premium Frontend Director](https://github.com/AVL05/premium-frontend-director) remains independent.

## 9. Hybrid autonomy and permissions

Routine, reversible work may proceed within the user's request. Approval is required before destructive actions, consequential architecture changes, risky dependency changes, migrations, production changes, publishing, or deployment.

See [autonomy and safety](autonomy-and-safety.md).

## 10. Collaboration rules

- Use the minimum useful number of specialists.
- Give every delegation a goal, acceptance criteria, scope, constraints, file ownership, and expected evidence.
- Parallelize only independent work; avoid concurrent edits to the same files.
- Do not invent agent names or assume a team is installed.
- Keep delegation shallow. The Director remains accountable for integration and final delivery.

## 11. Validation and evaluation

The repository CI checks marketplace JSON, plugin manifests, source paths, and component frontmatter. This does not replace `claude plugin validate` or a clean installation test in Claude Code.

Agent-assisted workflows will be evaluated against a plain Claude Code baseline. See [evaluation strategy](evaluation-strategy.md).
