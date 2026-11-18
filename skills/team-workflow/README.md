# team-workflow

English · [Español](README.es.md)

Coordinate a software team's work from requirements through integration, connecting tasks, Trello cards, GitHub issues, branches, and pull requests.

## Getting started

Follow the [installation guide](../../docs/installation.md) and open the software project's checkout in Claude Code or Codex. Each teammate using the skill needs it installed in their environment or shared through the project's configured skill location.

Provide the project requirements and the GitHub repository and Trello board links you want to use. Connect the relevant accounts with access to those destinations. The skill uses available integrations and can use authenticated `gh` for GitHub. It also supports GitHub-only tracking, Trello-only tracking, and local planning and Git work.

Run `/team-workflow init` in Claude Code or `$team-workflow init` in Codex. The skill reads applicable `AGENTS.md`, `CLAUDE.md`, `CONTRIBUTING.md`, templates, and project conventions. It adapts to the team's integration branch and actual Trello lists, including additional review, QA, or deployment stages. When a destination or rule is unclear, it asks for the missing detail.

## Commands

Prefix every command below with `/team-workflow` in Claude Code or `$team-workflow` in Codex.

| Command | Example in Claude Code | Result |
| --- | --- | --- |
| `init` | `/team-workflow init` | Discover the project, team, tools, and working agreements. |
| `plan` | `/team-workflow plan` | Propose tasks, acceptance criteria, dependencies, and assignments. |
| `sync [task]` | `/team-workflow sync E1-03` | Reconcile authorized cards and issues and report affected records. |
| `start <task>` | `/team-workflow start E1-03` | Verify readiness and create or reuse the task branch. |
| `pr [task]` | `/team-workflow pr E1-03` | Check the work and prepare or publish the PR as requested. |
| `status [task]` | `/team-workflow status` | Summarize progress, evidence, blockers, and next actions. |
| `close <task>` | `/team-workflow close E1-03` | Verify integration and update authorized tracking records. |

`<task>` is required and `[task]` is optional. Identify a task with its existing project ID or its card or issue URL. For example, `E1-03` might mean the third task in the first epic. IDs such as `TW-014` are illustrative conventions. Use the identifiers agreed by your team. The skill asks when a task reference is ambiguous.

## Example project walkthrough

Suppose three teammates are assigned to build a booking application. They have a GitHub repository, a Trello board, and written requirements. Their integration branch is `develop`, and their board has Backlog, Ready, In progress, Code review, QA, and Done. The following examples use Claude Code. In Codex, replace `/team-workflow` with `$team-workflow`.

1. **Establish the project context.** Run `/team-workflow init` and provide the requirements, repository and board links, and any missing team information. The skill reads existing rules and identifies the integration branch, verified tracker destinations, stage mapping, and completion requirements. The team can ask it to save the agreed profile for future sessions.

2. **Agree on the tasks.** Run `/team-workflow plan`. The skill proposes a breakdown covering booking creation, availability, and cancellation, with acceptance criteria and dependencies. The team reviews the proposed owners and effort and adjusts the plan. For this example, `E1-03` is the booking cancellation task and depends on booking creation.

3. **Publish the agreed plan.** Authorize the specific tasks and assignments in the selected board and repository, then run `/team-workflow sync`. The skill creates or reuses cards and issues, records their shared identities, and adds reciprocal links. Repeating `sync` on the same state should reuse those records. If only one side was updated before an interruption, the skill reports the completed operation and resumes from confirmed records.

4. **Start a ready task.** Once booking creation is integrated, its teammate runs `/team-workflow start E1-03`. The skill checks the cancellation criteria and dependency evidence, then prepares a branch from verified `develop` using the repository's naming rules. With authorization to update Trello, it moves the card to In progress and reports the branch and card link. Unrelated local changes can be preserved through a separate worktree.

5. **Implement and verify.** Ask the agent to implement the cancellation task and run its relevant tests. When you request a commit, the skill follows the project's Conventional Commit rules, for example `feat(bookings): support cancellation`. It reports which checks ran and their results. Task preparation alone leaves implementation for a subsequent request.

6. **Prepare and publish the PR.** Run `/team-workflow pr E1-03` and specify whether to prepare the proposal or publish it. For an authorized publication, the skill verifies the work, pushes the branch as authorized, creates or reuses the PR toward `develop`, and links it to the task. It reports pending or failed checks. It can move the card to Code review and request eligible reviewers within the authorization you gave.

7. **Review, test, and integrate.** A teammate reviews the PR, optionally using `review-pr` if installed. The author addresses feedback in the task branch. The team follows its Code review and QA rules before merging. Request any agreed Trello transitions during this work. Required independent approvals and QA evidence remain part of the project's completion criteria.

8. **Verify and record completion.** After integration, run `/team-workflow close E1-03` and authorize the relevant tracker updates. The skill checks the merged PR, integration SHA, acceptance criteria, and required reviews and checks. Once those conditions are satisfied, it records the evidence, moves the card to Done, and closes the issue as applicable. If a condition is missing, it reports the remaining work before updating the trackers.

9. **Check progress throughout the project.** Run `/team-workflow status` for the overall picture or `/team-workflow status E1-03` for one task. The report identifies work in progress, blocked dependencies, PRs, and outstanding reviews or checks, with links to the evidence.

## Authorization and confirmed outcomes

Discovery, planning, and status reporting are read-only by default. The skill presents proposed cards, issues, and assignments before applying them. An approval already given for the exact actions and destinations remains usable within that scope. A local branch request authorizes branch preparation. Pushes and tracker changes require applicable authorization as well.

The skill confirms remote changes before reporting success and gives links to the affected records. When access is missing or an operation partially succeeds, it reports what happened and which step remains pending.

The maintainer reports successful use of this skill in real projects. Additional validation includes a live GitHub and Trello walkthrough. See [the validation scenarios](tests/scenarios.md) for simulated projects and recovery cases.
