# review-pr

Review a GitHub pull request, inspect CI, and draft a formal approval or change request. Follow the [installation guide](../../docs/installation.md), then invoke the skill in the repository you want to review.

- Claude Code: `/review-pr 94`
- Codex: `$review-pr 94`

Either tool can also take a full PR URL. The skill uses the available GitHub integration and can fall back to authenticated `gh`. If neither is available, provide a diff or other review evidence directly. The result will identify what could be verified.

The first response includes a recommendation and the proposed review text. To submit it, reply in the same conversation with an explicit instruction such as “Publish that change request on PR #94.” Submission requires a GitHub connection that can write formal reviews with the reviewed commit SHA. If the PR has changed, the skill prepares a new review for you to authorize.

See [validation scenarios](tests/scenarios.md) for examples that use simulated GitHub data.
