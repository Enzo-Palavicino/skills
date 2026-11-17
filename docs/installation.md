# Installation

Check the [catalog](../README.md) for an available skill. The steps below apply to a skill whose folder already contains a complete `SKILL.md`.

From the checkout's root directory, replace `<name>` with the skill directory name. Copy the entire directory so its supporting files stay available. Choose the destination for your tool and check that it does not already contain a folder or symbolic link with that name.

| Tool | Personal destination | Project destination |
| --- | --- | --- |
| Codex | `~/.agents/skills/<name>/` | `.agents/skills/<name>/` |
| Claude Code | `~/.claude/skills/<name>/` | `.claude/skills/<name>/` |

Project paths are relative to the project where you want to use the skill. After installing, open that project in your tool and check the available skills. To uninstall, remove the installed copy from the chosen destination.

For discovery and invocation details, see [Codex skills](https://learn.chatgpt.com/docs/build-skills) and [Claude Code skills](https://code.claude.com/docs/en/skills).
