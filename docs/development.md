# Skill development

Keep each skill in `skills/<name>/`. Use a lowercase name with hyphens between words. A ready skill needs a `SKILL.md` with YAML frontmatter containing `name` and `description`, followed by Markdown instructions. The `name` must match the directory, and the description should explain what the skill does and when to use it.

Keep the main instructions concise. Put longer procedures in `references/`, templates or other resources in `assets/`, and reusable executables in `scripts/` when needed. Link supporting files from `SKILL.md` where the agent needs them. Use `tests/` for scenarios that verify expected behavior.

Before marking a skill ready, validate it against the [Agent Skills specification](https://agentskills.io/specification), check its relative links, and run representative scenarios in the tools listed as supported. Use fixtures for scenarios involving external services.
