# Local installation review

- Source: https://github.com/cloudflare/security-audit-skill
- Pinned commit: c1c8a8c1471069fb0e188eeaff69b8e8db6564a8
- Reviewed: 2026-11-02
- License: MIT; upstream license retained in LICENSE.
- Upstream skill, workflow instructions and validator code inspected for installation. This is not a claim of a complete security audit of the upstream project.
- No package install, hooks, daemon, credentials or target audit executed during installation.
- Validators use built-in Node.js modules; no network client or shell execution in the two validator entry points.
- Target-controlled execution requires the upstream OS-enforced isolation controls. Full host access is not an adequate sandbox. If unavailable, inspect source and retain runtime-dependent leads as needs_validation.
- Upstream files remain unchanged; this note and LICENSE are local additions.
