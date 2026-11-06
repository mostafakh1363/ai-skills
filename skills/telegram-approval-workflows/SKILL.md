---
name: telegram-approval-workflows
description: Design and review Telegram bots, commands, callback routing, human-review gates, approval state machines, operator controls, and n8n handoffs. Use for Telegram bot design, approval workflows, command routing, inline buttons, persistent keyboards, help text, content review, asset review, or publishing gates.
---

# Telegram Approval Workflows

Make Telegram an operator interface, not the hidden source of truth.

## Required context

Read [references/state-machine.md](references/state-machine.md) before changing approvals or downstream automation. Read [references/operator-controls.md](references/operator-controls.md) before changing commands, callbacks, buttons, keyboards, or help text.

## Workflow

1. Identify the canonical item, current version, current state, actor, action, and downstream side effect.
2. Define allowed transitions and reject invalid, stale, duplicate, or unauthorized actions.
3. Route text commands and callback buttons to the same action handlers.
4. Re-read canonical state before applying a transition.
5. Record actor, action, item, version, previous state, new state, and time.
6. Keep content, asset, queue, and publishing approvals separate.
7. Test the exact command and callback paths with pinned or sandbox execution data.

## Rules

- Keep human review enforced unless the user explicitly changes the policy.
- Keep live publishing disabled unless explicitly authorized.
- Make callbacks idempotent and acknowledge already-applied actions safely.
- Use short opaque callback identifiers when platform limits require them, then resolve server-side.
- Never place secrets or sensitive payloads in callback data or chat messages.
- Update help, guide, keyboard, aliases, buttons, and documentation in the same task.
- Preserve a text-command fallback for important approval actions.

## Output

Return the command map, callback contract, state machine, authorization, idempotency, downstream handoffs, help updates, test cases, and activation boundary.
