---
name: testing-and-debugging
description: Reproduce failures, isolate root causes, design tests, and validate fixes across backend, frontend, mobile, data, integrations, and deployment boundaries. Use for bugs, failing tests, flaky behavior, incidents, regressions, test plans, or requests to prove a change works.
---

# Testing and Debugging

Use the smallest reliable experiment that can distinguish competing causes.

## Workflow

1. Record the expected behavior, observed behavior, environment, and exact evidence.
2. Reproduce the failure or explain why reproduction is unavailable.
3. Reduce the problem to the narrowest failing boundary.
4. Form testable hypotheses and disprove them one at a time.
5. Identify the root cause separately from symptoms and contributing conditions.
6. If a fix is authorized, make the smallest coherent change and add a regression test.
7. Select proportional validation using [references/validation-matrix.md](references/validation-matrix.md).
8. Report what passed, what failed, and what could not be run.

## Rules

- A diagnosis request does not authorize a code change.
- Preserve logs, error text, failing inputs, and environment differences as evidence without exposing secrets.
- Do not install dependencies unless explicitly authorized.
- Do not use production as the first test environment.
- Avoid changing multiple variables in one diagnostic experiment.
- Do not mark a bug fixed when only the symptom disappeared.
- For flaky failures, record frequency, timing, shared state, ordering, and concurrency.

## Output

Return:

1. Reproduction status.
2. Root cause and evidence.
3. Fix or recommended fix.
4. Regression coverage.
5. Validation results.
6. Remaining risks or environment limitations.
