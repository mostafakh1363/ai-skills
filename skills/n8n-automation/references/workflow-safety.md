# n8n Workflow Safety

## Before editing

- Identify the active workflow version and whether executions are running.
- Export or record the current safe version without credentials.
- Confirm which nodes can write, publish, message, bill, delete, or execute code.

## Data and credentials

- Use n8n Credentials references rather than literal tokens or headers.
- Remove credentials, webhook secrets, account identifiers, and sensitive sample payloads from exports.
- Minimize personal, financial, call, SMS, and transcript data in prompts and logs.

## Control flow

- Keep dependent node execution sequential.
- Route each action to one clear handler.
- Use stable action and status values.
- Make external writes idempotent and detect replayed webhook or callback events.
- Stop safely when required input, context, or credentials are missing.

## Failure handling

- Log workflow, action, status, duration, safe error summary, and timestamp.
- Bound retries and distinguish transient from permanent failures.
- Keep failed items recoverable without duplicating successful side effects.
- Notify an operator when human input or manual reconciliation is required.

## Activation

- Test the exact branch with pinned or sandbox execution data.
- Verify downstream systems and status transitions.
- Confirm kill switch, owner, and rollback path.
- Activate only after required approval and post-activation smoke checks.
