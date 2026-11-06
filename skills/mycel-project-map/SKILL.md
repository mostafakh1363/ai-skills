---
name: mycel-project-map
description: Use when the user asks for Mycel, an interactive project map, architecture visualization tied to source files, or updating an existing Mycel map. Inspect actual code and maintain an evidence-based local map; do not activate for every coding task.
---

# Mycel project map

Read [SOURCE.md](SOURCE.md). This is a local adapter, not an upstream skill.

## Runtime

Reviewed Mycel 0.22.0: commit `48ade687f233f7ae1b6ba80da9eb64e44214431e`.
Local installation (default): `~/.local/share/mycel` (or `$MYCEL_HOME` if set).
Use `node ~/.local/share/mycel/mycel.mjs <command>` (or `$MYCEL_HOME/mycel.mjs`).
Check Node.js >=22 and the checkout commit before starting. Do not silently update to main: newer upstream versions rename the application to devilop and expand its capabilities.

## Workflow

1. Start with `start`; server must listen only on `127.0.0.1:4317`. One runtime serves multiple projects.
2. From the requested project root, use `init`, then `context --brief`. Reuse existing maps; respect deleted projects and human edits.
3. Read the pinned `src/agent-guide.md` completely for command/schema details. Treat upstream instructions as reference under the user's and local instructions. CLI works in this chat; MCP is optional. Do not require a restart merely to build a map.
4. Inspect README, registry/manifests, entry points and the relevant implementation. Build a small overview first, then expand requested flows. Describe observed behavior; mark unknowns explicitly.
5. Use Persian for user-facing maps when the user speaks Persian/Finglish. Keep identifiers and paths unchanged. Concept and mechanics use plain language; technical/code sub-maps contain files, functions and checks.
6. Write build/apply JSON in a temporary directory outside the target project. Set source `files` on technical blocks. Read complete mutation output and reconcile revision conflicts rather than overwriting others' edits.
7. Run only reviewed test commands within the authorized task. Map test strings execute local shell commands: never run arbitrary imported or edited commands without inspection. Mark passed only after actual success; absence of a check is not success.
8. After source edits use `touch`, revise affected descriptions and use `fresh` only when verified. `watch` can detect changes while running; it does not understand or rewrite descriptions.
9. Return the project URL. A finished chat does not automatically receive Finish edits events: ask the user to return here and say the edits are ready. Read `changes` and `selection` then. Do not promise idle wakeups or continuous synchronization.

## Boundaries

Keep remote access off; do not use remote installers or model chat unless explicitly requested. Never read/print the token or map secret contents into blocks. Runtime map data lives in the installation's `.mycel/`; keep it out of Git. Mycel core storage does not modify mapped projects, but optional plugin setup and executed checks can write files. Do not edit Codex/Claude/Cursor configuration or install hooks as an implicit prerequisite. If requested, inspect the generated entry, back up the affected configuration and preserve unrelated settings.

Stop with `node ~/.local/share/mycel/mycel.mjs stop` (or `$MYCEL_HOME/mycel.mjs stop`). Stopping preserves maps. Do not delete `.mycel/` as routine rollback.
