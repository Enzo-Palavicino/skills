# team-workflow

Coordinate development across Git, Trello, and GitHub. Start in the software project's checkout after following the [installation guide](../../docs/installation.md).

- Claude Code: `/team-workflow init`
- Codex: `$team-workflow init`

| Command | Result |
| --- | --- |
| `init` | Identify the project, team, tools, and rules. |
| `plan` | Propose tasks, acceptance criteria, dependencies, and assignments. |
| `sync [task]` | Reconcile authorized cards and issues and report the affected records. |
| `start <task>` | Verify readiness and create or reuse the task branch. |
| `pr [task]` | Check the work and prepare or publish the pull request as requested. |
| `status [task]` | Show evidence of progress and remaining blockers. |
| `close <task>` | Verify integration and update authorized tracking records. |

For example, run `plan` with the project requirements. Review the plan, authorize creation in the intended board or repository, then run `sync`. Run `start TW-014` to prepare its branch and `pr TW-014` when it is ready for review. After the team merges the PR, `close TW-014` checks the project's completion rules and records the result in the trackers you authorize.

The skill works with GitHub only, Trello only for tracking, or both. Local planning and Git branch work can continue with Git when neither tracker is configured. `gh` is optional. Remote changes require a connection with the appropriate access. The skill reports confirmed actions and their links, including where a step needs access or further input.

See [the validation scenarios](tests/scenarios.md) for simulated projects and recovery cases.
