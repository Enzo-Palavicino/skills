# Project setup and planning

## init

1. Discover the Git checkout, remotes, project instructions (`AGENTS.md`, `CLAUDE.md`, `CONTRIBUTING.md`), PR and issue templates, requirements, test commands, and existing team configuration. For a project without Git yet, identify the directory and propose setup. Initialize only when asked.
2. Discover the GitHub repository, issues, PRs, and default branch if GitHub is in use. Use branch policy, current project instructions, and user direction to find the integration branch. A default branch of `main` can coexist with an integration branch of `develop`. Ask if the evidence conflicts or is insufficient for an operation that changes state.
3. If Trello is in use, resolve the actual board, lists, and membership. Map the team's stages to verified list IDs before moving a card. If there is no agreed mapping, propose Backlog, Ready, In progress, In review, and Done as stages and map them to existing lists with the user. Do not invent a board or create lists as part of discovery.
4. Record supported providers and identity mappings using the team's GitHub logins and Trello member IDs. Use maintainers, code ownership, and already confirmed team data where applicable. Ask for missing inputs only when they affect decisions, such as reviewer rules, who can be assigned, the deadline, or how the team defines Done.
5. Show a short project profile with sources: repository and branch, tracker destinations, stage mapping, team and reviewers, branch and commit conventions, requirements, checks, and readiness and closeout rules. Identify unverified details. Reuse any existing project record. If the user wants durable configuration and has no existing location, save the agreed profile in `TEAM_WORKFLOW.md` at the project root. Store references and service IDs only as appropriate for that repository's visibility and keep credentials out of the file.

## plan

1. Read existing cards and issues, then the supplied requirements and project docs. Include closed or archived work when checking for duplicates. Treat confirmed requirements as requirements and mark assumptions and recommendations separately. Raise disagreements between sources rather than deciding silently.
2. Reuse issue and card links, existing task IDs, and the team's hierarchy. Break larger work into independently reviewable slices with testable criteria. Map each task to a requirement and identify prerequisites, suggested owner, priority, relative effort, and areas likely to overlap with another task. Base assignments on known membership, availability, workload, and independent review needs. Leave ownership open where the evidence is missing.
3. Use the team's task template or [the supplied task template](../assets/task.md). Before making any new cards, issues, or assignments, show the specific tasks, targets, and proposed owners. Show what would be reused and what would be created or updated. Refer the approved operations to [synchronization](sync.md).

## status

Read only the systems relevant to the request. Follow task links across trackers and PRs without assuming that a card in Done or a closed issue proves integration. Summarize counts or task state, blockers and dependencies, open PRs, pending reviews or checks, and next actions. Include owner or team workload when known. Label disagreements between systems and inaccessible or stale data. For a single task, prefer a short timeline with links over project-wide totals. Make no changes.
