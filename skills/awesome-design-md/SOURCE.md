# Awesome DESIGN.md source review

- Upstream: https://github.com/VoltAgent/awesome-design-md
- Source commit: `f6961238d5cddcf8042a74a70fc400ec67181abb`
- Source path: `design-md/*/DESIGN.md`
- License: MIT (see `LICENSE`)
- Reviewed: 2026-09-22

The upstream repository is a design-reference collection, not a Codex skill. This approved package adds a local adapter skill and vendors the 74 `DESIGN.md` files present at the pinned commit. Upstream per-brand README files, repository metadata, marketing content, and contribution files are excluded because they are not needed by coding agents.

## Review evidence

- The vendored source set contains 74 Markdown design references totaling 2,150,035 bytes.
- No upstream scripts, executables, symlinks, binary assets, credentials, or remote media are included.
- A scan found no prompt-override phrases, hidden control characters, or bidirectional Unicode controls.
- Thirty-four references contain `npx @google/design.md lint DESIGN.md` iteration suggestions. Two describe literal `curl | shell` install commands as UI content. The adapter treats every embedded command as non-executable reference data.

## Boundaries

- These files analyze public brand visuals; they do not grant rights to proprietary logos, fonts, photography, copy, or trademarks.
- The selected reference guides visual translation only. Project instructions, existing brand sources, security rules, accessibility requirements, and user authorization remain authoritative.
- Registry approval covers only this adapter and the pinned files. Review the upstream diff, content, and license again before changing the source commit.


## Public mirror note

This public repo includes the adapter skill, license, and catalog index.
Full per-brand `DESIGN.md` files remain at the upstream commit above; load only the selected brand when needed.
