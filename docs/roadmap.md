# Roadmap

This roadmap describes intended work. A milestone is complete only when its acceptance criteria are met and the repository reflects the implementation.

## M0 — Product and architecture foundation

- [x] Define full software-lifecycle scope.
- [x] Define Core + independently installable domain teams, technology packs, and optional skills.
- [x] Define the three-level operating model.
- [x] Define hybrid autonomy and approval boundaries.
- [x] Define evidence-first evaluation principles.
- [ ] Validate the target native Claude Code marketplace/plugin layout.

## M1 — Core plugin

- [ ] Create and validate the marketplace manifest.
- [ ] Package a minimal Core plugin.
- [ ] Implement the cross-domain `engineering-director`.
- [ ] Add baseline project planning and architecture capabilities.
- [ ] Verify specialist discovery, delegation, and graceful fallback.
- [ ] Test clean installation, update, and removal.

## M2 — Frontend team

- [ ] Migrate the current frontend prototype into an independently installable plugin.
- [ ] Finalize frontend architect, implementer, design, accessibility, and performance specialists.
- [ ] Keep Premium Frontend Director independent and optional.
- [ ] Validate the team with reproducible frontend fixtures.

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

- [ ] Publish independent first-party skill plugins where they add distinct value.
- [ ] Document third-party skill integrations without copying or auto-installing them.
- [ ] Test Premium Frontend Director as an optional independent companion.
- [ ] Document compatibility, installation scope, and fallback behavior.

## M6 — Evaluation and release

- [ ] Build repeatable baseline-versus-agent-assisted evaluation fixtures.
- [ ] Publish transparent results, including failures and limitations.
- [ ] Add CI validation for manifests, agent frontmatter, and package structure.
- [ ] Publish installation and contribution documentation.
- [ ] Tag a public release only after clean-install tests pass.

## Release policy

Do not mark a team stable merely because its agent files exist. A team needs clear responsibilities, documented permissions, working installation, at least one reproducible evaluation path, and honest compatibility notes.
