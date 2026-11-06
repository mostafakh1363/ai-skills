# Reviewed source

- Repository: https://github.com/mathew5612/mycel
- Version: Mycel 0.22.0
- Commit: 48ade687f233f7ae1b6ba80da9eb64e44214431e
- Reviewed: 2026-11-02
- License: MIT (bundled LICENSE)
- Adapter is locally authored; runtime stays outside project checkouts.

Inspected package manifest, agent guide, CLI/tool execution references and server host/origin/token/loopback handling. This is a scoped integration review, not a full security audit. No runtime npm dependencies. Local test commands can execute processes; remote and model modes have additional capabilities and remain outside this integration.

At inspection, upstream main was 8104593f96cbb7583f3c0a4e06bb2cbd373c2dde (devilop 0.26.1). The pinned Mycel version intentionally matches the requested map tool; re-review before upgrading.
