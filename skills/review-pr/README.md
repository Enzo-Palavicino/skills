# review-pr

English · [Español](README.es.md)

Review a GitHub pull request, inspect CI, and draft a formal approval or change request. Follow the [installation guide](../../docs/installation.md), then open the agent in the repository you want to review.

## Commands

| Agent | Command inside the conversation |
| --- | --- |
| Claude Code | `/review-pr 94` |
| Codex | `$review-pr 94` |

The number identifies a PR in the current repository. Either tool can also take a full PR URL. The skill uses the available GitHub integration and can fall back to authenticated `gh`. If access is missing, provide a diff or other review evidence directly. The result identifies what could be verified.

## Review workflow

1. Invoke the skill with the PR you want to review.
2. The agent reads context, applicable project rules, the diff, and CI. It presents findings, the reviewed revision, a recommended verdict, and the proposed review body.
3. To submit that proposal, reply in the same conversation with an explicit instruction such as “Publish that change request on PR #94.”
4. Before submitting, the agent checks that the commit and base branch match the reviewed revision. If either changed, it prepares a new review for authorization.
5. After publication, it verifies the formal review and returns its link. Submission requires a GitHub connection that can write reviews anchored to the reviewed commit.

## Verdicts and evidence

The skill recommends `APPROVE` or `REQUEST_CHANGES` based on verified defects. It can return `BLOCKED` when evidence is insufficient or `COMMENT_ONLY` for advisory observations. The result distinguishes CI, tests actually run, and pending checks.

## Validation

The maintainer reports successful use of this skill in real projects. The [validation scenarios](tests/scenarios.md) also cover simulated GitHub data, including authorization, changed revisions, and recovery after uncertain publication results.
