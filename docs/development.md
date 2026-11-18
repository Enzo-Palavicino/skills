# Skill development

Keep each skill in `skills/<name>/`. Use a lowercase name with hyphens between words. A ready skill needs a `SKILL.md` with YAML frontmatter containing `name` and `description`, followed by Markdown instructions. The `name` must match the directory, and the description should explain what the skill does and when to use it.

Keep the main instructions concise. Put longer procedures in `references/`, templates or other resources in `assets/`, and reusable executables in `scripts/` when needed. Link supporting files from `SKILL.md` where the agent needs them. Use `tests/` for scenarios that verify expected behavior.

Before marking a skill ready, validate it against the [Agent Skills specification](https://agentskills.io/specification), check its relative links, and run representative scenarios in the tools listed as supported. Use fixtures for scenarios involving external services.

Maintain `README.md` and `README.es.md` together in the repository root and each skill folder, with reciprocal language links. Keep runnable skill instructions in a single shared `SKILL.md`. Human-facing guides should explain where to install the skill, where to enter its commands, supported connections, and verified limitations.

This catalog is maintained by the repository owner. Follow [the maintenance policy](../CONTRIBUTING.md) and preserve the enforced [access controls](governance.md).
