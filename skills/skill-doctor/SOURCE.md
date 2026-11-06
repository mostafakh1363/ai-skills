# skill-doctor provenance

- Source: `warpdotdev/common-skills`, `.agents/skills/skill-doctor/`
- Commit: `69b4753651ab7fab518c82be087b9f1d5b966631`
- Upstream license: MIT (`LICENSE` in this directory)
- The bundled `assets/pierre-diffs.js` includes `@pierre/diffs` code under Apache-2.0; its license is retained as `skill-doctor/assets/pierre-diffs.LICENSE.md`.
- Added to the `ai-brain` registry profile. This does not install the skill in every local Codex project.

The collector reads local agent transcripts and writes a report to a temporary directory when invoked. Do not publish generated reports or transcripts without inspecting them for private data.
