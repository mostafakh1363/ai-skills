# Headroom adapter source review

- Upstream: https://github.com/headroomlabs-ai/headroom
- Source commit: `94206e265203acfd72a3b939e9a964e29175ad50`
- Upstream tag and package version: `v0.38.0` / `headroom-ai==0.38.0`
- License: Apache-2.0 (see `LICENSE` and `NOTICE`)
- Reviewed: 2026-09-22

The upstream repository is a Python, Rust, and TypeScript runtime rather than a Codex skill. This approved package contains only an AI Brain adapter, provenance, and upstream license notices. It does not vendor, install, import, or execute the Headroom runtime.

## Review coverage

The static review inspected the pinned release metadata, README, `pyproject.toml`, `SECURITY.md`, Codex wrapper and rollback paths, Codex provider and MCP registration, proxy bind defaults, TLS context construction, telemetry beacon, update checker, and optional-dependency advisories.

- The proxy and wrapper default to `127.0.0.1`, but remote binding is configurable. The adapter requires loopback verification.
- The anonymous usage beacon is on by default and the PyPI update check is also opt-out. The adapter disables both for privacy-sensitive evaluation and verifies the reported state.
- `headroom wrap codex` can write marker-delimited MCP entries in the active Codex config, read local authentication metadata from `auth.json` to distinguish ChatGPT OAuth from API-key mode, and register Serena unless `--code-memory none` is used. The adapter requires a config-only backup and prohibits exposing credential contents.
- The wrapper and Codex MCP registrar honor `CODEX_HOME`. The persistent provider helper in `headroom/install/paths.py` resolves `~/.codex/config.toml` directly, so persistent deployment with a non-default `CODEX_HOME` is blocked until that path is re-verified in a newer release.
- `HEADROOM_TLS_STRICT=0` clears only OpenSSL's `VERIFY_X509_STRICT`; chain, signature, expiry, and hostname verification remain enabled. The adapter keeps strict mode by default and treats relaxation as an explicit corporate-CA exception.
- Upstream's `SECURITY.md` at this commit lists 0.27.x as supported even though the release is 0.38.0. It also records unresolved advisories in optional CrewAI/ChromaDB and voice-training/Accelerate extras. The adapter therefore avoids `[all]` and installs only the selected mode's exact extra.

## Verification limits

- The commit and `v0.38.0` tag were fetched from the official GitHub repository; no signed tag or commit signature was verified.
- No package installation, provider-authenticated request, proxy startup, Codex config mutation, or end-to-end compression benchmark was performed during this registry review.
- Upstream performance and accuracy numbers remain vendor claims until reproduced on the user's workload.

Review upstream code, release artifacts, resolved dependencies, license notices, and the Codex integration diff again before changing the pinned version or enabling additional extras.
