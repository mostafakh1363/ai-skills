---
name: security-review
description: Review code, configuration, architecture, and operational changes for security weaknesses. Use for authentication, authorization, secrets, user-controlled input, file access, network calls, webhooks, databases, production operations, sensitive personal or financial data, or an explicit security audit.
---

# Security Review

Perform an evidence-backed security review without expanding the requested scope.

## Workflow

1. Identify assets, actors, entry points, trust boundaries, and sensitive data.
2. Trace user-controlled or external input from ingestion to storage, output, and side effects.
3. Inspect authentication, authorization, validation, secret handling, logging, and failure behavior.
4. Check the relevant items in [references/checklist.md](references/checklist.md). Read the full checklist for broad audits, pre-release reviews, or production-facing changes.
5. Confirm each finding against code, configuration, tests, or authoritative documentation.
6. Report prioritized findings and the smallest safe remediation.

## Review rules

- Treat diagnosis and remediation as separate permissions. Do not modify code during a review unless the user also asks for fixes.
- Never print or copy secret values. Report only the secret type, location, and remediation.
- Distinguish confirmed vulnerabilities from defense-in-depth improvements and unverified concerns.
- Do not claim exploitability without a plausible input, path, and impact.
- Check whether controls exist at the real enforcement boundary, not only in the UI.
- Prefer deny-by-default access, least privilege, bounded inputs, explicit allowlists, and auditable approvals.
- Verify time-sensitive security guidance against primary sources when internet access is available.

## Finding format

For every actionable finding include:

1. Priority: `P0`, `P1`, `P2`, or `P3`.
2. Location or affected surface.
3. Evidence and reachable failure path.
4. Security impact.
5. Minimal remediation.
6. Validation or regression test.

If no actionable finding is confirmed, say so and list any remaining coverage gaps.
