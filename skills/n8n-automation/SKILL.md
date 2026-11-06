---
name: n8n-automation
description: Design, inspect, debug, and validate n8n workflows, workflow JSON, webhooks, schedules, credentials, data mapping, retries, logging, and human-approval automation. Use for n8n nodes, executions, workflow routing, webhook integrations, Telegram orchestration, workflow imports or exports, and production automation safety.
---

# n8n Automation

Design workflows as explicit stateful systems with safe side effects.

## Workflow

1. Identify the trigger, inputs, outputs, state store, credentials, side effects, and owner.
2. Define the data contract between every node and sub-workflow.
3. Keep execution order explicit when downstream expressions depend on prior nodes.
4. Add idempotency, bounded retries, timeouts, error routing, and execution logging.
5. Separate read, draft, review, approve, and publish or apply stages.
6. Read [references/workflow-safety.md](references/workflow-safety.md) before changing production-facing, credentialed, publishing, or write workflows.
7. Read [references/approval-patterns.md](references/approval-patterns.md) for Telegram, human review, callbacks, or approval gates.
8. Test with pinned or sandbox data before activation and verify the exact execution path.

## Rules

- Store credentials only in n8n Credentials or the approved secret manager.
- Sanitize workflow exports before saving them to Git.
- Never assume a node output shape; inspect execution data or documentation.
- Avoid parallel branches that later depend on each other's node data.
- Use one canonical status vocabulary and normalize external values at ingestion.
- Prevent duplicate external writes with stable keys and idempotency checks.
- Do not activate publishing, billing, messaging, or destructive workflows without explicit approval.
- Preserve existing human-review gates unless the user explicitly changes the policy.

## Output

For designs or reviews return:

1. Trigger and data contract.
2. Ordered node or sub-workflow plan.
3. State transitions.
4. Credential and security boundaries.
5. Error, retry, and idempotency behavior.
6. Test and activation checklist.
7. Remaining approval requirements.
