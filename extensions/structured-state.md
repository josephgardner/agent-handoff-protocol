# Structured state (optional proposal)

JSON, YAML frontmatter, or other machine-readable metadata MAY be introduced when another tool actually consumes it. Avoid mandatory duplicate state.

Potential fields: protocol identifier, capability declarations, workspace identifier, checkpoint references, and last verification time. None is normative yet. If a structured projection conflicts with `HANDOFF.md`, stop and reconcile rather than guessing which representation is newer.
