# Validation Matrix

## Pure logic

- Run focused unit tests for normal, boundary, invalid, and regression inputs.
- Prefer deterministic clocks, IDs, and fixtures.

## API and services

- Verify status codes, response schema, validation, authorization, idempotency, and downstream failure.
- Test service logic separately from route wiring when possible.

## Persistence

- Test empty, existing, duplicate, concurrent, partially migrated, and interrupted states.
- Verify migrations against a copy or fixture, never the only production data.

## Frontend and mobile

- Test rendering, user interaction, navigation, state restoration, permissions, and failure states.
- Use real-device or browser validation when platform behavior is part of the bug.

## Integrations

- Test contract parsing and safe failure with recorded or sandbox data first.
- Verify timeouts, retry limits, duplicate delivery, rate limits, and provider fallback.

## Deployment

- Run static checks and focused tests before build or deploy checks.
- Distinguish local checkout, deployed artifact, and live runtime evidence.
- Verify health, logs, and rollback readiness after an authorized deployment.
