# Product Vision

## One-sentence vision

Give Claude Code users a modular engineering team they can assemble around their project, with clear responsibilities, controlled autonomy, and quality claims backed by evidence.

## The problem

Agent collections often optimize for quantity: many overlapping role prompts, unclear ownership, duplicated instructions, and little proof that the agents improve delivery. Large all-in-one installations also force users to accept tools and workflows they may not need.

Claude Dev Agents should solve a different problem: provide a small, coherent Core and independently installable specialists that work together without requiring every component.

## Who it is for

- Individual developers using Claude Code on real projects.
- Full-stack developers who need different specialist teams across projects.
- Teams that want repeatable engineering workflows and review gates.
- Open-source contributors who want to add or improve a specialist pack.

## Product principles

1. **Modularity:** users decide which teams, technology packs, and skills to install.
2. **Clear ownership:** every agent has a bounded mission, inputs, outputs, and constraints.
3. **Useful without add-ons:** optional skills enrich the workflow but never become hidden requirements.
4. **Hybrid autonomy:** routine work is streamlined; consequential actions remain under user control.
5. **Evidence-first quality:** tests, builds, browser checks, and evaluation results support claims.
6. **Technology awareness:** inspect the actual repository; do not assume a framework.
7. **Efficiency:** avoid unnecessary agents, duplicated context, and redundant reviews.
8. **Open collaboration:** document contribution rules, licenses, and compatibility.

## Scope

The long-term scope covers the software development lifecycle: product planning, architecture, frontend, backend, databases, testing, security, DevOps/platform engineering, AI engineering, mobile, and data engineering.

Delivery will be incremental. The first release validates Core and a Frontend team; later teams are added only after their workflows and evaluations are ready.

## Non-goals

- Building a new agent runtime outside Claude Code.
- Replacing developers or removing human accountability.
- Automatically installing third-party skills, dependencies, or services.
- Claiming that more agents always produce better results.
- Supporting every framework before there is a tested specialist for it.
- Promising guaranteed production quality or autonomous deployment.

## Success criteria

- A new user can understand the package choices and install only what they need.
- Core works without optional skills.
- A domain team can be installed and removed independently.
- Agents delegate only to available specialists and do not invent capabilities.
- Hybrid approval boundaries are clear and consistently followed.
- Reproducible evaluations show where agent-assisted workflows help, fail, or add overhead.
- Documentation and releases accurately describe compatibility and limitations.
