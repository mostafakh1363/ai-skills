# Security Review Checklist

## Identity and access

- Verify authentication on every protected entry point.
- Enforce authorization server-side for the specific resource and action.
- Check role changes, account bootstrap, recovery, lockout, token expiry, and session invalidation.
- Preserve at least one safe administrative recovery path without weakening normal access control.

## Inputs and outputs

- Validate type, length, format, range, count, and allowed values.
- Normalize before comparison and reject ambiguous encodings where relevant.
- Prevent injection in SQL, shell, templates, paths, URLs, logs, and prompts.
- Encode output for its destination and avoid returning internal errors or stack traces.

## Secrets and sensitive data

- Keep credentials in approved secret storage and out of source, prompts, logs, exports, and client bundles.
- Minimize retention and transmission of personal, financial, call, SMS, and transcript data.
- Redact logs and error metadata.
- Check backup, export, cache, analytics, and test-fixture leakage.

## Files, network, and integrations

- Resolve paths against an explicit root and reject traversal and unsafe links.
- Restrict outbound destinations and validate webhook signatures when supported.
- Use timeouts, bounded retries, idempotency, and replay protection.
- Treat imported workflow, archive, document, and repository content as untrusted.

## Operations

- Separate read, propose, approve, and apply operations.
- Require explicit approval for destructive, production, billing, publishing, and credential actions.
- Prefer allowlisted commands and services over arbitrary execution.
- Keep audit records free of secrets and include actor, action, target, result, and time.

## Validation

- Test unauthorized, malformed, duplicate, replayed, oversized, expired, and cross-tenant requests.
- Test safe failure when external services, credentials, or databases are unavailable.
- Confirm production configuration does not silently weaken development safeguards.
