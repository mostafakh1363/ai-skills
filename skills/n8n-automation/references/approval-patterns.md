# Human Approval Patterns

## State model

Use explicit states such as:

```text
draft -> pending_review -> approved -> queued -> completed
                      \-> rejected
                      \-> revision_required
```

Never infer approval from message delivery, button rendering, or workflow success alone.

## Callback and command handling

- Include a stable item ID and intended action in callbacks.
- Re-read current state before applying the transition.
- Reject stale, duplicated, unauthorized, or invalid transitions.
- Make callbacks idempotent and return the already-applied result safely.
- Keep commands and buttons mapped to the same action handler.

## Publishing boundary

- Treat content approval, asset approval, queue preparation, and publishing as separate gates.
- Require all prerequisite approvals before queueing.
- Keep live publishing disabled until explicitly authorized.
- Record who approved what, when, and from which current version.

## Operator experience

- Keep help text, keyboards, buttons, aliases, and documentation synchronized.
- Show current status and the next allowed actions.
- Provide clear rejection and revision paths.
- Avoid exposing secrets or sensitive payloads in chat messages.
