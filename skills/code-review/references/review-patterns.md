# Code Review Patterns

## Backend and API

- Keep routes thin and move business rules into services or use cases.
- Validate inputs and return consistent status codes and response shapes.
- Check transaction boundaries, retries, idempotency, pagination, and concurrency.
- Verify authorization at the resource and action boundary.
- Confirm errors do not leak secrets or convert business failures into ambiguous success.

## Data and migrations

- Preserve existing data and provide forward migrations for schema changes.
- Verify constraints, indexes, nullability, defaults, and rollback or recovery behavior.
- Check serialization, units, timestamps, currency precision, and identifier stability.
- Test old data, empty data, duplicates, partial records, and interrupted writes.

## Frontend and mobile

- Keep business logic out of rendering components.
- Check loading, empty, success, error, permission, and offline states.
- Verify navigation, state restoration, accessibility, responsive behavior, and RTL where applicable.
- Confirm UI controls map to real backend or domain enforcement.

## Integrations and operations

- Check timeouts, retries, rate limits, provider fallback, and safe metadata logging.
- Preserve environment separation and keep credentials server-side.
- Verify deployment assumptions, health checks, and failure recovery.
- Require explicit approval for production mutations and external side effects.

## Tests

- Prefer behavior-focused tests at the lowest layer that proves the requirement.
- Cover happy path, edge cases, failure path, and the reported regression.
- Avoid mocks that bypass the behavior under review.
