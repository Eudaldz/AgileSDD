---
example: true
ticket_id: "T-002"
title: "Explain safe adoption and independent handoff"
type: "documentation"
priority: "high"
story_points: 3
status: "done"
revision: 1
depends_on: ["T-001"]
external_refs: []
approval:
  state: "approved"
  by: "Illustrative project owner"
  evidence: "Illustrative decision D-002: approve the specific specification and plan; not actual authorization"
---
# T-002: Explain safe adoption and independent handoff

> Illustrative example. Decisions, actors, branches, snapshots, and historical checks below are teaching records, not actual approvals, Git objects, or executed history.

## Metadata

Frontmatter owns ticket-level metadata. All approval/state history is illustrative.

## Summary

Let a developer start from the public template or adopt it into an existing project while preserving project state and independent acceptance.

## Problem / Objective

The documentation baseline alone does not explain sample replacement, agent invocation differences, or the boundary between implementation and independent review.

## Scope

Root README entry points and a detailed adoption/daily-use guide, plus a clear review handoff.

## Out of Scope

Installer, CLI, publishing/release tooling, package manifests, tests, demo applications, and remote PR creation.

## Requirements

- FR-001: Explain template-copy and manual-copy entry paths without package installation.
- FR-002: Explain replacing sample state while preserving existing documentation, source, application tests and ticket history.
- FR-003: Explain independent reviewer handoff and pending acceptance when no reviewer is available.
- NFR-001: Use ordinary project docs and valid local links; require no agent-specific SDK.

## Acceptance Criteria

- AC-001 (FR-001, NFR-001): README explains copying reusable directories, skill discovery fallback, and no-install adoption; verify instructions against the actual paths.
- AC-002 (FR-002): The adoption guide explicitly preserves real project docs/source/tests/tickets and does not inherit sample approvals; inspect the existing-project and sample-replacement instructions.
- AC-003 (FR-003): The guide explains fresh reviewer or independent human handoff and leaving acceptance pending when unavailable; inspect it against the review policy.

## Dependencies

[T-001](../T-001/specification.md) supplies the accepted illustrative baseline. Real implementation must check its actual dependency evidence, not inherit this sample completion.

## Constraints

Use the [constitution](../../docs/constitution.md) and [ADR-001](../../docs/decisions/ADR-001-repository-native-template.md). Normal work cannot edit reusable directories.

## Assumptions

Developers have their own editor/agent. Explicitly reading a SKILL.md is the discovery fallback; universal agent discovery is not assumed verified.

## Open Questions

None for this illustrative scope. Cross-agent compatibility research remains separately tracked in [T-003](../T-003/specification.md).

## Related Documentation

[README](../../README.md); [adoption guide](../../docs/development/adoption.md); [workflow](../../docs/workflow.md).

## Change History

Illustrative revision 1: D-002 approves scope and plan after baseline completion; draft -> specified -> planned. TASK-001 is implemented then reviewed independently. TASK-002 builds on it, reaches in_review, returns to in_progress for F-001, then returns to in_review with a corrected boundary. R-003 accepts both tasks and full ticket; reviewer records accepted -> done after checking docs. The specification is unchanged by the fix; no requirement/approval was weakened.
