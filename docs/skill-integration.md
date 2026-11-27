# Optional Skill Integration Policy

## Purpose

Claude Dev Agents provides specialist agents and engineering workflows. Skills provide additional knowledge or procedures. Users must remain free to choose which skills they install and use.

## Rules

1. **No mandatory third-party skills.** Every team must have a useful baseline workflow without external companions.
2. **User choice.** Never install, update, or remove a skill on the user's behalf without explicit approval.
3. **No vendoring by default.** Do not copy external skill files, scripts, assets, or documentation into this repository.
4. **Respect ownership and licenses.** Link to the original source and follow its license and installation instructions.
5. **No assumed availability.** A skill mentioned in documentation or a prompt is not proof that it is installed or callable in the current session.
6. **Task-based selection.** Use only skills relevant to the current task; avoid stacking several tools with overlapping or contradictory guidance.
7. **Graceful fallback.** If an optional skill is unavailable, use the team's built-in workflow and report the limitation only when it materially affects the result.
8. **Compatibility evidence.** Mark integrations as tested only after a reproducible installation and invocation test with a stated Claude Code version.

## Premium Frontend Director

[Premium Frontend Director](https://github.com/AVL05/premium-frontend-director) is an independent project maintained separately from this repository.

- It is not bundled into Claude Dev Agents.
- Users may install it independently through its own documented distribution method.
- Frontend agents may use it when the user has installed it and it is available in the current Claude Code session.
- The base frontend workflow must remain useful without it.
- Do not duplicate its canonical skill, references, assets, or scripts in this repository.

## External skills catalogue

A future compatibility catalogue may list optional skills by category:

- Design and creative direction.
- Framework-specific engineering.
- Accessibility and UX review.
- Testing and browser automation.
- Security and secure coding.
- Performance and observability.
- AI engineering and evaluation.

Each entry must include the original repository, maintainer, license, installation instructions, compatibility status, and a concise explanation of when it is useful. A catalogue entry is a recommendation, not an automatic dependency.

## Invocation discipline

Agents must not claim that a companion skill was used unless it was actually available and invoked. If the host does not expose a reliable way to discover or invoke a skill, the agent must not pretend otherwise. Ask the user to invoke or install it only when its specific contribution is important to the task.
