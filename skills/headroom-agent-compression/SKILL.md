---
name: headroom-agent-compression
description: Assess, install, configure, verify, and roll back Headroom for local AI-agent token compression. Use when the user mentions Headroom, headroomlabs-ai/headroom, agent context compression, or wants Headroom proxy, MCP, or Codex integration; do not treat advertised savings as guaranteed.
---

# Headroom Agent Compression

Headroom is a third-party runtime, proxy, library, and MCP server. It is not an upstream Codex Skill. This adapter provides a reviewed integration workflow; loading it does not install Headroom, start a proxy, or modify agent configuration.

## Source and evidence

1. Read [SOURCE.md](SOURCE.md) before recommending or applying an integration.
2. Use the upstream repository and documentation as the product authority, but keep installation pinned to a reviewed release.
3. Describe savings and accuracy as upstream benchmark results, not guarantees. Measure the user's representative workload before recommending broad use.
4. Keep these states separate: Skill available, package installed, proxy running, agent routed through the proxy, retrieval working, and savings measured.

## Safety boundaries

- Evaluation is read-only. Do not infer permission to install a package, edit `~/.codex/config.toml`, register MCP servers, start a background service, or wrap an agent.
- A direct request to install or configure Headroom authorizes only the named local integration. Preview affected paths, preserve a reversible backup, and avoid unrelated agent settings.
- Never print, copy, or directly inspect Codex `auth.json`, provider tokens, API keys, cookies, or credential stores. The reviewed Headroom release can read local authentication metadata while configuring Codex; disclose that before an authorized trial and never expose its contents.
- For `headroom wrap codex`, preserve the active `CODEX_HOME` and use the same value for rollback. At the reviewed release, do not use persistent `headroom deploy` with a non-default `CODEX_HOME`; its provider installer targets `~/.codex/config.toml` even though the wrapper and MCP registrar honor `CODEX_HOME`.
- Bind the proxy to loopback and verify the listener. Never expose it on `0.0.0.0`, a public interface, or a tunnel without a separate authentication and network review.
- Keep normal TLS verification and strict mode. `HEADROOM_TLS_STRICT=0` relaxes one RFC 5280 strictness flag for corporate CAs; use it only when the user explicitly needs that compatibility and the replacement CA path has been reviewed. Never use `verify=false` or an equivalent bypass.
- The anonymous beacon and update check are opt-out in the reviewed release. For privacy-sensitive use, set `HEADROOM_BEACON=off` and `HEADROOM_UPDATE_CHECK=off`, then verify the effective beacon state with `headroom telemetry --show`.
- For a Codex proxy trial, prefer the exact reviewed `headroom-ai[proxy]` version. Do not install `[all]`; it expands the dependency and advisory surface beyond the requested mode.
- Keep `--learn`, `--memory`, output shaping, code graph, and code-memory integrations off unless the user explicitly requests them. Use `--code-memory none` for the smallest Codex trial; Serena is otherwise registered by default.

## Workflow

1. Identify the target agent, authentication mode, operating system, CPU, Python and `uv` availability, existing proxy or custom provider, active `CODEX_HOME`, and whether Headroom is already installed.
2. Inspect configuration without printing secrets. For Codex, provider routing belongs in user-level configuration; project-local `.codex/config.toml` cannot safely substitute for the active user configuration.
3. Choose the least invasive mode that meets the request:
   - assessment: inspect only;
   - application library: integrate `compress()` in code;
   - MCP: expose explicit compression, retrieval, and stats tools;
   - proxy: route an OpenAI-compatible client;
   - agent wrapper: launch the named agent through Headroom.
4. Before installation, select and record a reviewed release. Prefer an isolated `uv tool` environment over system Python, pin the exact version, use only the required extras, and inspect newly resolved dependencies. Do not install from an unpinned branch.
5. Before a Codex wrapper test, back up only the active `config.toml`, record its checksum and permissions, and preview the intended diff. Do not back up or read `auth.json`.
6. Start with a non-sensitive project and temporary session. For the reviewed release, the smallest Codex trial is:

   ```text
   HEADROOM_BEACON=off HEADROOM_UPDATE_CHECK=off \
     headroom wrap codex --code-memory none
   ```

   The wrapper still registers Headroom's retrieval MCP in the active user configuration. Treat that write as part of the approved integration and verify unrelated MCP entries remain unchanged.
7. Verify the actual path, not only process startup:
   - `headroom doctor` reports healthy routing and retrieval;
   - the proxy listens only on loopback;
   - `headroom telemetry --show` reports the beacon disabled;
   - one representative request appears in Headroom stats;
   - the agent returns a correct result and can retrieve compressed source content;
   - `headroom perf` or the dashboard reports measured input/output counts;
   - native Codex behavior remains available after the wrapped session ends.
8. Compare baseline and Headroom runs on the same task. Report before/after tokens, compression ratio, latency, answer correctness, failures, and sample size. Do not generalize a JSON/log result to prose or already-dense context.

## Rollback

1. Stop the wrapped agent and local proxy.
2. Run `headroom unwrap codex` with the same `CODEX_HOME` used for setup, then compare the active config with the pre-change backup.
3. Restore only Headroom-owned changes if automatic rollback is incomplete; preserve unrelated settings and MCP servers.
4. Confirm normal Codex startup, provider selection, history visibility, and absence of Headroom routing.
5. Uninstall the isolated package only when the user also requests removal.

## Output

Lead with the observed outcome. Report the reviewed release, target agent, files changed, proxy bind address, telemetry state, verification results, measured savings, rollback result, and remaining risk. Never call the integration complete from installation output alone.
