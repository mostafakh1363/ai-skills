# Telegram Approval State Machine

## Recommended separation

```text
draft
  -> pending_content_review
  -> content_approved
  -> pending_asset_review
  -> asset_approved
  -> queue_ready
  -> publishing_approved
  -> published
```

Each review state must also support rejection, revision, expiry, and cancellation where applicable.

## Transition contract

Require:

- stable item ID
- current item version
- expected current state
- requested action
- authorized actor
- timestamp

Apply a transition only when all preconditions still match. Return the current canonical state for stale or duplicate callbacks.

## Approval boundaries

- Content approval does not approve graphics or other assets.
- Asset approval does not publish.
- Queue preparation does not publish.
- Workflow execution success does not equal human approval.
- Message delivery does not equal approval.

## Downstream handoff

Trigger one clearly named downstream action per accepted transition. Use idempotency keys so retries do not duplicate queue rows, messages, assets, or publications.
