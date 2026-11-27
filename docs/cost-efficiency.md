# Cost and Efficiency Policy

## Goal

Claude Dev Agents must make agent-assisted engineering useful without turning every task into a multi-agent workflow. Context overhead and additional model calls are product costs and must be measured.

## 1. Installation is opt-in per repository

Use `--scope local` by default. It enables the plugin for the current user in the current repository and stores the setting in `.claude/settings.local.json`.

Use `--scope project` only when the repository intentionally shares plugin activation with collaborators. Use `--scope user` only when a person explicitly wants the plugin across all projects.

Registering a marketplace adds its catalogue source to user settings. It does not enable its plugins. Only enabled plugins add components to a session.

## 2. Understand the two token footprints

Claude Code's `claude plugin details <plugin>` reports:

- **Always-on:** component names and descriptions included in context on every turn while the plugin is enabled.
- **On-invoke:** full agent or skill instructions loaded when the component is used.

Treat the estimates as configuration diagnostics, not exact billing forecasts. Record the CLI version, plugin version, and output when benchmarking.

## 3. Delegation tiers

The Engineering Director must choose the least expensive workflow that meets the task's risk and complexity:

| Tier | Example | Default agent use |
| --- | --- | --- |
| 0 — Tiny | Explanation, one-line edit, simple config change | No subagent |
| 1 — Standard | Focused bug fix or bounded feature | One implementer, or direct execution |
| 2 — Complex | Multi-step feature, uncertain architecture, significant refactor | One planner **or** architect if needed, then one implementer |
| 3 — High risk | Auth, security, data integrity, migrations, production changes | Relevant implementer plus one independent reviewer/auditor and objective tests |

Default budgets:
- Ordinary work: 0–2 subagent invocations.
- Complex work: up to 3 invocations when each has a distinct purpose.
- More than 3: only when user-requested or risk-justified; explain the reason.
- Default concurrency: 2; 3 only for independent tasks.
- One review pass by default.
- One correction/re-review pass only for blockers, major findings, or failed objective checks.
- Minor/polish findings are reported, not used to trigger repeated loops.

These are operating defaults, not hard technical limits.

## 4. Avoid duplicate work

- Do not ask multiple agents to inspect the same files for the same question.
- Do not invoke planner and architect by default for the same task.
- Do not invoke every frontend reviewer after every UI change.
- Prefer existing lint, type-check, tests, build, and browser evidence over repeated agent summaries.
- Use design review for meaningful visual changes, accessibility review for interactive/semantic changes, and performance audit only when performance is a requirement or likely regression.
- Keep agent handoffs concise: task, scope, acceptance criteria, constraints, and required evidence.
- Do not repeat a review when no relevant code changed.

## 5. Agent prompt design

- Keep frontmatter descriptions short, specific, and easy to route.
- Put detailed operating instructions in the agent body, which loads only when invoked.
- Give each agent a narrow responsibility and read-only tools unless it must edit.
- Do not preload optional skills into every agent.
- Prefer a small number of useful specialists over many overlapping roles.

## 6. Model strategy

Do not hardcode a more expensive model for every specialist. Let the user select the session model by default. Where a user wants a lower-cost profile, they can configure lightweight read-only planning/review agents to use an available lower-cost model and reserve their preferred coding model for implementation.

Model choice must be validated against task quality; never claim cost savings without comparing actual usage and outcomes.

## 7. Evaluation requirements

For each representative task, record:

- enabled plugins and their always-on estimates;
- agents/skills actually invoked and invocation count;
- on-invoke estimates for used components;
- model and Claude Code version;
- task completion and objective test results;
- elapsed time and any available usage/cost data;
- unnecessary or repeated delegations;
- baseline result without Claude Dev Agents.

Do not optimize token count at the expense of correctness, accessibility, security, or maintainability. Publish trade-offs and failures.

## 8. User controls

Users should be able to inspect, disable, uninstall, and selectively install plugins. Document these commands:

```powershell
claude plugin details cda-core@claude-dev-agents
claude plugin disable cda-frontend@claude-dev-agents --scope local
claude plugin enable cda-frontend@claude-dev-agents --scope local
claude plugin uninstall cda-frontend@claude-dev-agents --scope local
```
