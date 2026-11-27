# Roadmap

This roadmap describes intended work. A milestone is complete only when its acceptance criteria are met and the repository reflects the implementation.

## M0 — Product and architecture foundation

- [x] Define full software-lifecycle scope.
- [x] Define Core + independently installable domain teams, technology packs, and optional skills.
- [x] Define the three-level operating model.
- [x] Define hybrid autonomy and approval boundaries.
- [x] Define evidence-first evaluation principles.
- [x] Add a preview marketplace manifest and initial plugin package manifests.
- [ ] Pass Claude Code's native marketplace/plugin validation and a clean-install test.

## M1 — Core plugin

- [x] Package a Core plugin preview.
- [x] Add the cross-domain `engineering-director`.
- [x] Add baseline planning, architecture, general implementation, and code review agents.
- [ ] Verify specialist discovery, delegation, and graceful fallback in Claude Code.
- [ ] Test clean installation, update, and removal.

## M2 — Frontend team

- [x] Package a Frontend team preview.
- [x] Add frontend architect, implementer, design reviewer, accessibility auditor, and performance auditor.
- [x] Keep Premium Frontend Director independent and optional.
- [ ] Validate agent discovery and delegation from the Core Director.
- [ ] Evaluate the team with reproducible frontend fixtures.

## M3 — Additional domain teams

Implement incrementally, with distinct responsibilities and tests:

- [ ] Backend engineering.
- [ ] Database engineering.
- [ ] Quality engineering and testing.
- [ ] Security engineering.
- [ ] DevOps and platform engineering.
- [ ] AI engineering and agentic systems.
- [ ] Mobile and data engineering, subject to demonstrated demand.

## M4 — Technology packs

- [ ] React / Next.js.
- [ ] Node.js / TypeScript.
- [ ] Laravel / PHP.
- [ ] Python / FastAPI.
- [ ] Vue / Nuxt.
- [ ] Angular and Svelte / Astro, after evaluation.

## M5 — Optional skill ecosystem

- [x] Publish initial first-party frontend quality, design review, and accessibility skill plugins.
- [ ] Document third-party skill integrations without copying or auto-installing them.
- [ ] Test Premium Frontend Director as an optional independent companion.
- [ ] Document compatibility, installation scope, and fallback behavior.

## M6 — Evaluation and release

- [x] Define baseline-versus-agent-assisted evaluation methodology.
- [ ] Build repeatable evaluation fixtures and automated checks.
- [ ] Publish transparent results, including failures and limitations.
- [ ] Add CI validation for manifests, agent frontmatter, and package structure.
- [ ] Publish installation and contribution documentation.
- [ ] Tag a public release only after clean-install tests pass.

## Release policy

Do not mark a team stable merely because its agent files exist. A team needs clear responsibilities, documented permissions, working installation, at least one reproducible evaluation path, and honest compatibility notes.
