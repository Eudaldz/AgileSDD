---
example: true
ticket_id: "T-001"
title: "Establish the documentation baseline"
type: "documentation"
priority: "high"
story_points: 3
status: "done"
revision: 1
depends_on: []
external_refs: []
approval:
  state: "approved"
  by: "Illustrative project owner"
  evidence: "Illustrative decision D-002: approve the specific specification and plan; not actual authorization"
---
# T-001: Establish the documentation baseline

> Illustrative example. Decisions, actors, branches, snapshots, and historical checks below are teaching records, not actual approvals, Git objects, or executed history.

## Metadata

Frontmatter owns ticket-level values. Approval/state history is illustrative only.

## Summary

Give a developer enough project context to navigate and safely adapt this documentation-only template.

## Problem / Objective

Without a constitution and current architecture, a fresh session could infer nonexistent services or treat example approvals as real. Establish a file-backed documentation baseline.

## Scope

Project purpose, constitution, workflow options, current architecture, a component description, a template-only ADR, and a documentation index.

## Out of Scope

Application code, runtime tooling, CLI, installation, publishing, framework tests, and remote integrations.

## Requirements

- FR-001: Document purpose, constraints, verification/review rules and file-based architecture with real repository paths.
- FR-002: Provide navigation to all baseline documents and the template-only decision.
- NFR-001: Clearly label teaching state and distinguish current files from proposed/unverified behavior.

## Acceptance Criteria

- AC-001 (FR-001): The baseline documents describe no application runtime and cite existing files; verify by reading project, constitution, workflow, architecture and component docs.
- AC-002 (FR-002): The documentation index links the complete baseline and ADR; verify every local target.
- AC-003 (NFR-001): Sample artifacts explain their illustrative status; verify frontmatter/banner and no claimed real approval.

## Dependencies

None.

## Constraints

Follow the [constitution](../../docs/constitution.md), [constraints](../../docs/architecture/constraints.md), and illustrative [ADR-001](../../docs/decisions/ADR-001-repository-native-template.md). No source/runtime scaffold.

## Assumptions

The sample project is the template itself; current file existence is evidence, while historical acceptance is illustrative.

## Open Questions

None for the illustrative scope.

## Related Documentation

[Documentation index](../../docs/README.md); [workflow](../../docs/workflow.md).

## Change History

Illustrative revision 1: owner D-001 selects template-only architecture; D-002 approves specified scope and technical plan. Planner moves draft -> specified -> planned after contracts are checked. Implementer records planned -> in_progress -> in_review. Reviewer R-001 verifies all tasks/criteria, records accepted, then done after documentation completion. These decisions are not actual user approvals.
