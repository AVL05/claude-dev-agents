# Evaluation Strategy

## Objective

Demonstrate whether Claude Dev Agents improves software delivery compared with using Claude Code without this repository's agents. The project must not rely on agent self-ratings or invented benchmark scores.

## Evaluation approach

Use repeatable tasks in small fixture repositories. For each task, compare:

- **Baseline:** Claude Code with the same model, task brief, repository, and available tools, but without Claude Dev Agents.
- **Agent-assisted:** the same task and conditions with the relevant Core/team plugins enabled.

Keep model choice, task prompt, fixture commit, tool permissions, and validation commands as consistent as practical. Record deviations.

## Evaluation dimensions

| Dimension | Evidence |
| --- | --- |
| Task completion | Acceptance criteria satisfied or not |
| Functional correctness | Existing and added tests; reproducible manual checks |
| Build and static quality | Lint, type-check, build, and static analysis outputs |
| Regression risk | Regression tests and reviewer findings |
| Maintainability | Structured human review using a published rubric |
| Security | Relevant automated checks and documented manual review |
| Accessibility | Automated checks plus manual keyboard/semantic review where applicable |
| Visual quality | Matched browser screenshots and a documented human rubric |
| Efficiency | Wall-clock time and observable tool/agent activity; token/cost data only when reliably available |
| Reliability | Failure modes, recovery, unsupported assumptions, and repeat-run consistency |

Do not combine all dimensions into one opaque score. Publish raw results, scoring rules, environment, limitations, and representative failures.

## Initial evaluation fixtures

Start with a small set of frontend tasks because the repository's first implemented team is frontend:

1. Fix a responsive overflow bug without changing unrelated components.
2. Implement a form with loading, success, and validation-error states.
3. Add an accessible navigation interaction.
4. Refactor a duplicated component while preserving behavior.
5. Improve a measured performance bottleneck without regressing functionality.
6. Redesign a page against a brief and verify the actual rendered result.

Later add fixtures for API authorization, database migration safety, test coverage, deployment configuration, and AI tool-use workflows as those teams are implemented.

## Quality gates

A task is not considered successful merely because an agent says it is complete. Require the relevant objective checks and record any checks that could not be run.

- Tests and build commands must actually execute.
- Browser-based claims require captured browser evidence.
- Security and accessibility claims must state the scope and limitations of the checks.
- Human rubric scores must identify the reviewers and criteria.
- A failed run must remain in the report; do not silently discard it.

## Reproducibility

Each evaluation record should include:

- evaluation ID and date;
- repository fixture and commit SHA;
- exact task prompt;
- Claude Code version and model, where available;
- installed plugins, agents, and optional skills;
- tool permissions and environment;
- commands executed and raw results;
- screenshots or logs where applicable;
- known limitations and reviewer notes.

## CV and portfolio evidence

Useful evidence for a professional portfolio includes architecture documentation, agent specifications, installation tests, CI runs, reproducible evaluation reports, issue/PR history, and a demonstration using a real project.

Do not describe the project as improving productivity or code quality until evaluations support that claim. Do not claim expertise from installing or prompting agents alone; demonstrate design, implementation, testing, evaluation, and maintenance of the system.
