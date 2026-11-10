# Multi-agent coordination (optional proposal)

Concurrent agents MAY use ownership boundaries, checkpoints, leases, or a coordinator. This extension must define how conflicting writes are detected and resolved before claiming safe concurrency.

No agent should silently overwrite another agent's newer handoff. Cross-repository and remote-state claims require independent reconciliation.
