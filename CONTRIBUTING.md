# Contributing

Thanks for helping improve Claude Dev Agents.

## Before contributing

- Read the relevant agent, skill, and [quality standards](docs/quality-standards.md).
- Inspect existing resources before proposing a new one; avoid overlapping specialists.
- Keep each specialist narrow, with explicit scope, inputs, outputs, and escalation rules.
- Do not assume a framework, package manager, test runner, or browser automation tool unless the target project confirms it.

## Agent definition checklist

A good agent definition should state:

1. Its mission and when to use it.
2. What context it must inspect first.
3. A step-by-step workflow.
4. Constraints and anti-patterns.
5. Expected deliverables and reporting format.
6. What it must not claim without evidence.

## Pull requests

- Keep changes focused and explain the problem they solve.
- Update documentation when behavior or responsibilities change.
- Validate Markdown and YAML syntax where practical.
- Never include credentials, private project data, or generated secrets.
- Report validation commands accurately; distinguish not run from passed.
