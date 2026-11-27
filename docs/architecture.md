# Modular Architecture

## 1. Product scope

Claude Dev Agents targets the full software development lifecycle while remaining modular. It is built specifically for Claude Code and relies on Claude Code's native extension mechanisms.

The system is not a standalone agent runtime, hosted service, or framework generator. Claude Code remains the execution environment.

## 2. Distribution model

One public GitHub repository will host one Claude Code marketplace. The marketplace will expose independently installable plugins grouped into four categories:

1. **Core plugin** — shared orchestration and baseline engineering capabilities.
2. **Domain team plugins** — specialists for software disciplines.
3. **Technology plugins** — framework/language-specific expertise.
4. **Skill plugins** — optional, focused workflows and methods.

The final marketplace manifest and plugin manifests will be added only after the package layout is validated against the current Claude Code plugin specification.

### Proposed repository layout

```text
.claude-plugin/
  marketplace.json
plugins/
  core/
    .claude-plugin/plugin.json
    agents/
    commands/
    skills/
  teams/
    frontend/
      .claude-plugin/plugin.json
      agents/
      skills/
    backend/
    database/
    quality/
    security/
    devops/
    ai-engineering/
    mobile/
    data-engineering/
  technology/
    react-nextjs/
    vue-nuxt/
    angular/
    svelte-astro/
    node-typescript/
    laravel-php/
    python-fastapi/
  skills/
    design-quality/
    testing-strategy/
    accessibility/
    api-design/
docs/
evaluations/
fixtures/
.github/workflows/
```

This is a target layout, not a claim that every directory or plugin already exists. The first implementation will validate the Core and Frontend packages before expanding.

## 3. Installation composition

- Users install the Core plugin and only the domain teams they need.
- Technology packs add focused guidance for the stack in use.
- Skill plugins are independent and optional.
- A full-stack setup is assembled by installing the relevant frontend, backend, database, and quality/security components.
- No team may silently install another plugin or third-party skill.
- Plugin dependencies must be explicit, minimal, and documented. Prefer graceful degradation over mandatory companion dependencies.

The project will not create duplicate "full-stack" versions of frontend and backend specialists. Cross-domain tasks are coordinated by the Director using the specialists available in the current Claude Code session.

## 4. Three-level operating model

### Level 1 — Director

The Core `engineering-director` is the primary entry point for cross-domain tasks. It:

- translates the request into acceptance criteria;
- inspects repository instructions and the actual stack;
- selects only installed and relevant specialists;
- sequences dependent work and parallelizes only independent work;
- defines file ownership and delegation boundaries;
- integrates specialist reports and owns the final handoff.

A domain-focused director (for example, the existing frontend director prototype) may be retained as a specialist profile or workflow where it adds distinct value. It must not create redundant layers of coordinators.

### Level 2 — Specialists

Specialists own bounded responsibilities and return concrete implementation or evidence. Planned domain teams include:

| Team | Example responsibilities |
| --- | --- |
| Frontend | UI implementation, design systems, responsive behavior, accessibility |
| Backend | APIs, business logic, authentication, integrations |
| Database | Data modeling, migrations, query performance, data integrity |
| Quality | Test strategy, unit/integration/E2E testing, regression analysis |
| Security | Threat modeling, secure coding, dependency and configuration review |
| DevOps / Platform | CI/CD, deployment configuration, observability, infrastructure |
| AI Engineering | Model integration, agent workflows, retrieval, tool use, evaluations |
| Mobile | Mobile application architecture and platform-specific implementation |
| Data Engineering | Pipelines, data quality, storage and transformation |

Only teams with distinct responsibilities and validated workflows should be added.

### Level 3 — Quality control

Quality control is a cross-cutting gate coordinated by the Director. It selects relevant reviewers and objective checks based on risk.

Examples:
- UI changes: visual, responsive, accessibility, and functional checks.
- API changes: contract, authorization, validation, and integration tests.
- Database changes: migration safety, integrity, and query checks.
- AI features: task success, groundedness, tool-use correctness, refusal/safety behavior, and regression evaluations.
- Deployments: build, configuration, smoke tests, rollback readiness, and explicit approval.

A report is not proof that a check passed. The system records commands run, results observed, and checks not run.

## 5. Technology specialists

The Core and domain teams should be technology-agnostic wherever possible. Technology packs add only the knowledge that is specific to a framework, runtime, or language.

Examples include React/Next.js, Vue/Nuxt, Angular, Svelte/Astro, Node.js/TypeScript, Laravel/PHP, and Python/FastAPI.

Do not create a separate agent for every minor library. Add a technology pack only when it has a distinct workflow, concrete examples, and evaluation cases.

## 6. Optional skill ecosystem

Skills are not mandatory dependencies of the agent teams.

- A user may install a skill from this marketplace, another marketplace, or a compatible external source.
- The user chooses whether and when to invoke it.
- External skills remain under their original maintainers and licenses.
- The project may document tested integrations, but must not copy or automatically install third-party content.
- Agents must have a useful baseline workflow when optional skills are absent.
- Do not preload every optional skill into every agent; load only task-relevant knowledge to control context use and avoid conflicting instructions.

[Skill integration policy](skill-integration.md) documents the rules. Premium Frontend Director remains independent at https://github.com/AVL05/premium-frontend-director.

## 7. Hybrid autonomy and permissions

The system may autonomously perform routine, reversible actions within the user's request. Approval is required before destructive actions, consequential architecture changes, risky dependency changes, migrations, external publication, production changes, or deployment.

See [autonomy and safety](autonomy-and-safety.md).

## 8. Collaboration rules

- Use the minimum useful number of specialists.
- Give each delegation a goal, acceptance criteria, scope, constraints, file ownership, and expected evidence.
- Never allow concurrent agents to edit the same files without explicit coordination.
- Do not invent an agent name or assume a team is installed. If a specialist is unavailable, perform the task within the current capability or report the limitation.
- Keep delegation shallow. The Director remains accountable for integration and final delivery.
- Preserve project conventions and avoid unnecessary dependencies or rewrites.

## 9. Current implementation boundary

The current repository contains an initial frontend prototype under `.claude/`. This is a development starting point, not the final marketplace layout. The first technical milestone is to validate the native Core + Frontend plugin packaging, installation, agent discovery, and clean removal before adding further domain teams.
