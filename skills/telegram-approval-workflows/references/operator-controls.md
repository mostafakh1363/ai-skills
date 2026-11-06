# Telegram Operator Controls

## Command design

- Keep a small stable set of primary commands.
- Use aliases only when they map to the same handler.
- Separate navigation commands from state-changing commands.
- Require an item identifier or selected current item for state changes.
- Confirm destructive or externally visible actions.

## Buttons and callbacks

- Show only actions allowed in the current state.
- Keep callback payloads bounded and free of secrets or personal data.
- Expire or safely reject old buttons.
- Answer callbacks promptly and perform longer work asynchronously where needed.
- Edit or follow up on the original message with the canonical result.

## Help synchronization

When commands, buttons, aliases, or behavior change:

- update `/help` and control-center copy
- update persistent and inline keyboards
- update project documentation
- test text commands and callback routes
- verify progress and error messages

## Safety pattern

For content automation, preserve human gates between topic, content, platform, graphic or asset, queue, and publishing stages. Keep the publisher disconnected or disabled until the owner explicitly authorizes live publishing.
