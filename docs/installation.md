# Installation

English · [Español](installation.es.md)

## Download the catalog

Run these commands in your terminal from a directory where you keep repositories.

```bash
git clone https://github.com/Enzo-Palavicino/skills.git
cd skills
```

Both skill folders should contain a `SKILL.md` before installation. Copy the whole folder so references and templates are included.

## Install in one project

Run the block below from the cloned catalog's root. Replace `project_dir` with the absolute path to the software project where you want the skills. Set `tool_dir` to `.claude` for Claude Code or `.agents` for Codex. Run it once for each agent if you use both.

```bash
(
  set -eu
  project_dir="/absolute/path/to/your/project"
  tool_dir=".claude"
  test -d "$project_dir"

  for skill in review-pr team-workflow; do
    test -f "skills/$skill/SKILL.md"
    destination="$project_dir/$tool_dir/skills/$skill"
    if [ -e "$destination" ] || [ -L "$destination" ]; then
      echo "Already installed: $destination. Inspect it before updating."
      exit 1
    fi
  done

  mkdir -p "$project_dir/$tool_dir/skills"
  for skill in review-pr team-workflow; do
    cp -R "skills/$skill" "$project_dir/$tool_dir/skills/"
  done
)
```

Committing the project skill directories makes the installed versions available to teammates who clone that project, subject to its repository rules.

## Install for your user

From the catalog root, use the same checks with a personal destination. Choose `~/.claude/skills` for Claude Code or `~/.agents/skills` for Codex.

```bash
(
  set -eu
  install_dir="$HOME/.claude/skills"
  for skill in review-pr team-workflow; do
    test -f "skills/$skill/SKILL.md"
    destination="$install_dir/$skill"
    if [ -e "$destination" ] || [ -L "$destination" ]; then
      echo "Already installed: $destination. Inspect it before updating."
      exit 1
    fi
  done
  mkdir -p "$install_dir"
  for skill in review-pr team-workflow; do
    cp -R "skills/$skill" "$install_dir/"
  done
)
```

## Invoke in your project

Open a session in the target project's directory. Launch Claude Code with `claude` or open the project in Codex. Enter the following in the agent's conversation.

| Agent | Initialize the project | Review a PR |
| --- | --- | --- |
| Claude Code | `/team-workflow init` | `/review-pr 94` |
| Codex | `$team-workflow init` | `$review-pr 94` |

The PR number refers to that project's GitHub repository. A full PR URL also identifies a review target. If a newly installed skill is missing, start a new agent session in that project.

## Connections, updates, and removal

Connect GitHub and Trello in each agent as needed. Authenticated `gh` can fill GitHub capability gaps. Confirm the intended repository or board when authorizing external changes.

Copied skills stay at the installed revision. To update, download the desired catalog revision, compare it with the installed copy, preserve any project changes, and replace it deliberately. To uninstall, remove the specific skill directory from the installation destination.

[Codex skills](https://learn.chatgpt.com/docs/build-skills) · [Claude Code skills](https://code.claude.com/docs/en/skills)
