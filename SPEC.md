# Agent Handoff Protocol — V4 Draft

**Status:** Proposal, not a published standard. **Version:** 4.0-draft.

## 1. Purpose and scope

This protocol enables a person or agent to resume interrupted work from a durable, portable handoff. It applies to software, research, writing, design, and offline workflows. It does not require Git, a network, a task tracker, a particular model, or a particular agent runtime.

The key words **MUST**, **MUST NOT**, **SHOULD**, and **MAY** express requirements for implementations claiming conformance to this draft.

## 2. Core artifact

A conforming workspace MUST provide a human-readable Markdown document named `HANDOFF.md`. This is the canonical *execution handoff*, not necessarily the source of truth for code, task status, approvals, or evidence.

A handoff MUST communicate, either directly or through locally available references:
- **Objective:** what outcome is sought.
- **Current state:** what is known, completed, uncertain, or blocked.
- **Next action:** a bounded, actionable continuation.
- **Constraints and authority:** prohibited changes, required approvals, and scope limits.
- **Verification:** how to check whether the next action succeeded.

It SHOULD record consequential decisions and references to evidence. Headings and ordering are not normative; implementations MUST interpret the meaning rather than require exact headings. An empty or unknown field MUST be expressed as unknown or not yet determined, not silently invented.

## 3. Lifecycle

1. **Orient.** Read `HANDOFF.md` and any applicable local instructions. Identify referenced sources and whether they are accessible.
2. **Reconcile.** Inspect the actual environment before trusting potentially stale claims. Treat the handoff as a claim about execution state, not proof that work was done.
3. **Execute.** Select only work within the stated authorization and constraints. Do not infer approval from a passing test or a prior agent's suggestion.
4. **Verify.** Record relevant evidence, failures, and unresolved uncertainty. Never represent unrun checks as passed.
5. **Handoff.** Update durable state when it materially changes, including incomplete work and the next safe action. Preserve information needed for recovery; avoid copying entire transcripts.

When a referenced dependency is unavailable, an agent MUST distinguish verified local facts from unverified external claims and MUST NOT silently advance blocked work.

## 4. Sources of truth

Each fact SHOULD have a clear canonical owner. `HANDOFF.md` owns the execution cursor and summarizes or links to other sources. Code and tests own implementation facts; a task tracker may own backlog status; approval records own approvals; evidence artifacts own detailed results.

Conflicting sources MUST be surfaced rather than silently overwritten. Agents MUST NOT rewrite external canonical records merely to make them agree with the handoff.

## 5. Portability and extensions

A minimal installation is a single `HANDOFF.md`. No frontmatter, schema, command, issue tracker, or auxiliary file is mandatory.

Extensions MAY provide task tracking, structured metadata, validation, evidence retention, multi-agent coordination, or workspace checkpoints. Extensions MUST NOT redefine core safety and authority requirements. Optional integrations SHOULD degrade gracefully when offline; where safe continuation is impossible, the handoff SHOULD state the blocker.

Agents MAY detect existing tooling, but MUST NOT assume permission to create external issues, push commits, publish, or deploy. Extensions requiring external writes or elevated authority need appropriate authorization.

## 6. Conformance

A conforming **handoff document** includes the five core semantic fields in §2, with uncertainty made explicit.

A conforming **agent workflow** can read that document, reconcile it with available evidence, respect authority boundaries, verify its work, and update the handoff without requiring any optional extension.

This draft intentionally does not prescribe a parser, serialization schema, exact heading names, or an automatic discovery algorithm.

## 7. Open questions

- Should the filename be strictly uppercase `HANDOFF.md`, or should case-insensitive discovery be allowed?
- How should competing handoffs be selected in multi-directory workspaces?
- Should a machine-readable capability declaration be standardized, and if so, where?
- What constitutes conformance evidence for agents with limited filesystem access?
- What migration guarantees should apply to V3 artifacts?

See [extensions](extensions/README.md), [examples](examples/README.md), and [V3 migration notes](history/v3-migration.md).
