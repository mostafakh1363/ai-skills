# AI Skills (public)

A clean, shareable collection of **generic** agent skills for coding, review, security, automation, design, and tooling.

This repository is intentionally public-safe. Project-specific and business-private skills live elsewhere and are not mirrored here.

## What's inside

| Skill | When to use |
| --- | --- |
| `code-review` | Review code changes, diffs, PRs for correctness and regressions. |
| `testing-and-debugging` | Reproduce failures, isolate root causes, design tests, validate fixes. |
| `security-review` | Review auth, secrets, input handling, and sensitive data flows. |
| `n8n-automation` | Design, inspect, debug, and safely operate n8n workflows. |
| `telegram-approval-workflows` | Design Telegram bots with human-review gates and approval state machines. |
| `project-data-analyst` | Analyze project files, spreadsheets, emails, and notes into actionable insights. |
| `ponytail` | Default coding style: prefer existing code, stdlib, native features, smallest correct change. |
| `emil-design-eng` | Apply Emil Kowalski design-engineering guidance for polished web UI and motion. |
| `headroom-agent-compression` | Assess/install/verify/roll back Headroom agent context compression. |
| `mycel-project-map` | Build evidence-based interactive project architecture maps with Mycel. |
| `jev-ultrafast` | Fast structured-DOM browser automation with reviewed Jev + Microsoft Edge. |
| `security-audit` | Full security audit workflow and attack-class checklists (Cloudflare skill). |
| `skill-doctor` | Grade agent skills from real conversation history for efficiency and compliance. |
| `awesome-design-md` | Apply a reviewed brand-inspired DESIGN.md visual system from the Awesome DESIGN.md catalog. |
| `ui-ux-pro-max` | UI/UX design intelligence; load full data from the public ui-ux-pro-max-skill repo. |

## How agents should use this repo

1. Read [`INDEX.md`](INDEX.md) (or follow [`AGENTS.md`](AGENTS.md)).
2. Pick skills that match the task.
3. Open those `SKILL.md` files and follow them.
4. Say which skills you used.

## Using with Cursor / Claude / GPT / Grok

### Cursor
- Add this repo as a readable dependency in your Cloud Agent environment, **or**
- Copy / submodule `skills/` into your project's `.cursor/skills` (or equivalent), **or**
- Put a short rule in the project `AGENTS.md`: "Before coding work, read https://github.com/mostafakh1363/ai-skills/blob/main/INDEX.md and load matching skills."

### Claude Code / Codex-style skill folders
- Copy selected skill folders into your personal or project skills directory so the harness auto-discovers `SKILL.md` packages.

### ChatGPT / GPT projects
- Paste `AGENTS.md` + the relevant `SKILL.md` into project instructions, or attach this repo if your workspace supports GitHub.

### Grok / other agents
- Same pattern: give the agent `INDEX.md` + instruct it to open matching skills before acting.

## Pointers (not fully vendored here)

- **ui-ux-pro-max** data tables: https://github.com/mostafakh1363/ui-ux-pro-max-skill
- **awesome-design-md** brand `DESIGN.md` files: https://github.com/VoltAgent/awesome-design-md (see skill `SOURCE.md` for pinned commit)

## License / attribution

First-party skills in this mirror are provided for reuse. Third-party approved skills keep their upstream `LICENSE` / `SOURCE.md` / `NOTICE` files—preserve them when you copy a skill out.

## Security

Do not commit secrets, tokens, private hosts, personal paths, or customer data into forks of this repository.
