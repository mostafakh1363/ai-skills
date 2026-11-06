---
name: code-review
description: Review code changes, diffs, pull requests, modules, or repositories for correctness, regressions, architecture violations, maintainability, and missing tests. Use when the user asks for a code review, PR review, implementation audit, regression check, or release-readiness review.
---

# Code Review

Review behavior and risk, not formatting preferences.

## Workflow

1. Establish the requested scope, intended behavior, and relevant project instructions.
2. Inspect the diff and enough surrounding code to understand callers, state, persistence, and error paths.
3. Trace changed behavior through API, domain, data, UI, and operational boundaries as applicable.
4. Check tests and documentation against the actual behavior.
5. Use [references/review-patterns.md](references/review-patterns.md) for the affected stack or change type.
6. Report only findings that are actionable and supported by evidence.

## Review rules

- Prioritize correctness, data loss, security, user-visible regressions, and operational failure.
- Do not treat a different valid implementation style as a defect.
- Verify that a suspected issue is reachable before reporting it.
- Keep line ranges tight and explain the concrete failure scenario.
- Do not modify files unless the user also asks to address the findings.
- Respect dirty worktrees and do not attribute unrelated changes to the reviewed task.
- If no actionable findings are confirmed, say so and identify untested or uninspected risk areas.

## Finding format

For each finding include:

1. Priority: `P0` through `P3`.
2. Short title.
3. File and smallest useful line range.
4. Failure scenario and impact.
5. Suggested correction.
6. Test that would prevent regression.

Keep summaries secondary to findings.
