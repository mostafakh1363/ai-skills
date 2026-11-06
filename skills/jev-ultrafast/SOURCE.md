# Jev Ultrafast source review

- Upstream: https://github.com/browser-use/jev-ultrafast
- Source commit: `1231850a0bf1a0c0341fe408ef1668dbbfdfac46`
- Upstream version: `0.1.0`
- License: MIT (see `LICENSE`)
- Reviewed: 2026-09-21

The upstream repository is a Python browser runtime, not a Codex skill. This approved package contains an AI Brain adapter skill, provenance, and the upstream license. It does not vendor or install the runtime. Any authorized runtime setup must use a disposable checkout at the exact commit above and the committed `uv.lock` with `uv sync --frozen`.

## Review evidence

The review traced the action loop, DOM snapshot, browser execution, model requests, local inspector, secret inputs, output validation, and the Browser Harness daemon/CDP entry paths used by Jev. The locked `browser-harness==0.1.13` wheel matched SHA-256 `2491459e4bfc0ee8aea22dc6c4680fc0f791b7ba553446323c50d2883449d769`.

At the pinned commit, these upstream checks passed in a disposable environment with telemetry disabled:

- `uv run ruff check .`
- `uv run pytest` — 31 tests passed
- `node --check jev_ultrafast/static/app.js`
- `node --check jev_ultrafast/snapshot.js`
- `uv build`

Microsoft Edge compatibility was also verified locally on macOS with Edge `153.0.4234.48`, a dedicated temporary profile, a loopback-only CDP endpoint, and no account data. `/json/version` identified the browser as `Edg/153.0.4234.48` with CDP protocol `1.3`; `scripts/check_guards.py` passed all 21 browser guard checks without model calls or external websites. The isolated Browser Harness daemon was stopped and the temporary Edge profile was removed after the test.

No paid-provider run was performed because that requires provider credentials and would transmit task and page context externally.

## Security boundaries

- Jev sends visible page state and goal context to TypeSafe; text-field context is sent to the configured OpenAI-compatible provider.
- Browser Harness can control an existing Edge profile and its authenticated sessions. The adapter therefore defaults to a dedicated Edge automation profile and verifies that the connected CDP endpoint identifies itself as `Edg/`.
- Browser Harness has opt-out telemetry and a CLI update check. The adapter disables both for every setup and runtime command.
- The local inspector binds to `127.0.0.1`, validates the Host header, requires a per-process token for writes, bounds request size, and serializes browser steps.
- Model output is restricted to observed operation/target choices; text output must be a bounded JSON string. This reduces but does not eliminate prompt-injection or wrong-action risk.
- Registry approval covers this adapter and guarded use of the pinned commit. It is not approval of later upstream commits, arbitrary model endpoints, a shared personal Edge profile, or externally consequential actions.

Review the upstream diff, lockfile, dependency artifacts, provider behavior, and license again before changing the pinned commit.
