# V3 preservation and migration notes

This repository proposes a V4 handoff-first contract informed by the earlier [Agent Session Protocol article](https://algoplay.com/agent-session-protocol/) and its linked V3 materials.

**This is not a verbatim V3 archive.** The complete original V3 specification must be imported and checked against its source before this repository claims to preserve it.

Proposed conceptual mapping (subject to verification against the original):
- `BOOT.md` → orientation procedure in the core lifecycle.
- `STATE.json` → optional structured-state extension.
- `NEXT.md` → next-action section of `HANDOFF.md`.
- Queue → optional task-tracking extension.
- `TRACKER.md` → optional evidence/history extension.

Migration SHOULD preserve original records, approvals, and evidence. It MUST NOT silently discard unresolved blockers or rewrite history. Existing V3 projects need not migrate to use the V4 concepts.
