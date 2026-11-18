# Skills

English · [Español](README.es.md)

Reusable Agent Skills for Codex and Claude Code, maintained by Enzo Palavicino. Review pull requests and coordinate software delivery using your project's rules and the tools available to your agent.

## Skill catalog

| Skill | Purpose | Availability |
| --- | --- | --- |
| [review-pr](skills/review-pr/README.md) | Inspect a PR, its diff and CI, then draft a verdict and submit the review after authorization. | Preview |
| [team-workflow](skills/team-workflow/README.md) | Connect planning, Trello cards, GitHub issues, branches, PRs, and closeout. | Preview |

Both skills have usable instructions. Preview indicates that project-specific behavior still needs validation in your environment. The Team Workflow walkthrough was tested with a private GitHub repository and a Trello board. Its test project had no CI checks. Review PR has been checked with simulated scenarios.

## Install and use

Clone this repository, then copy the complete skill folders into your agent's personal skill location or the target project's skill directory. The [installation guide](docs/installation.md) includes commands that check existing installations before copying.

| Agent | Personal installation | Project installation | Invoke inside the agent |
| --- | --- | --- | --- |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` | `/team-workflow init` or `/review-pr 94` |
| Codex | `~/.agents/skills/` | `.agents/skills/` | `$team-workflow init` or `$review-pr 94` |

Launch the agent from the software project you want to work on. Enter the skill command in the agent's conversation. Claude Code interprets the slash command. Your terminal shell is used for installation and launching the agent.

GitHub CLI (`gh`) is an optional fallback. GitHub and Trello operations depend on authenticated connections and permissions in the agent you are using. Configure each agent's account connections in that environment.

## Repository layout

```text
skills/
├── .github/
│   └── CODEOWNERS
├── docs/
│   ├── installation.md
│   ├── installation.es.md
│   ├── development.md
│   └── governance.md
├── skills/
│   ├── review-pr/
│   │   ├── SKILL.md
│   │   ├── references/
│   │   └── tests/
│   └── team-workflow/
│       ├── SKILL.md
│       ├── references/
│       ├── assets/
│       └── tests/
├── README.md
├── README.es.md
├── CONTRIBUTING.md
├── SECURITY.md
├── AGENTS.md
└── LICENSE
```

Each skill follows the [Agent Skills specification](https://agentskills.io/specification) with a `SKILL.md` entrypoint. Supporting procedures live in `references/`, reusable templates in `assets/`, and behavioral scenarios in `tests/`. English and Spanish README files provide human-facing guidance alongside the shared skill instructions.

## Maintenance and security

Enzo Palavicino administers this repository and its issues, PRs, branches, and releases. Everyone can read and install the published skills under the MIT License. Repository permissions and rulesets enforce the maintenance policy. Read the [governance details](docs/governance.md), [maintenance policy](CONTRIBUTING.md), and [security policy](SECURITY.md).

## License

[MIT](LICENSE) · Copyright © 2026 Enzo Palavicino.
