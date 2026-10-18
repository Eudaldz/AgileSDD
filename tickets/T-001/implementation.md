---
example: true
ticket_id: "T-001"
spec_revision: 1
plan_revision: 1
plan_status: "approved"
planned_on: "2026-10-18"
approval:
  state: "approved"
  by: "Illustrative project owner"
  evidence: "Illustrative decision D-002: approve the specific specification and plan; not actual authorization"
---
# Implementation: T-001

> Illustrative example. Decisions, actors, branches, snapshots, and historical checks below are teaching records, not actual approvals, Git objects, or executed history.

## Metadata

Frontmatter identifies the illustrative plan approval. Specification owns ticket status.

## Specification Reference

[Specification](specification.md), revision 1; [review contract](review.md), contract revision 1.

## Existing Context

Read [constitution](../../docs/constitution.md), [overview](../../docs/architecture/overview.md), [workflow](../../docs/workflow.md), and [ADR-001](../../docs/decisions/ADR-001-repository-native-template.md). Only repository text is present; no application is inferred.

## Human Direction

Illustrative owner direction for iteration 1: document the actual file-based template, name its boundaries, and label all sample approvals as teaching records. Do not invent an application or introduce tooling. D-002 approves this concrete baseline plan, not unspecified future iterations.

## Iteration Scope

Iteration 1 creates the project baseline, architecture, workflow and decision documentation in TASK-001. No runtime code, tests, CLI or publishing work is proposed.

## Finding Assessment

No review exists before this first iteration. TASK-001 maps to the fixed specification; independent review will check actual deliverables.

## Technical Approach

Write baseline project docs against current reusable files. There is no runtime, migration, data model or application interface. Record the illustrative template-only decision as an ADR.

## Architecture Impact

No runtime architecture change. The docs describe current file boundaries, with teaching history visibly illustrative. ADR-001 constrains scope; no additional decision or source migration is needed.

## Acceptance Criteria

Use the exact canonical AC IDs and wording from the [specification revision 1](specification.md). Task mappings below and the [review contract](review.md) cover every criterion without redefining it.

## Ordered Tasks

### TASK-001

```yaml
id: "TASK-001"
title: "Document the current template architecture"
status: "accepted"
depends_on: []
acceptance_criteria: ["AC-001", "AC-002", "AC-003"]
supporting_work: null
files: ["docs/README.md", "docs/project.md", "docs/constitution.md", "docs/workflow.md", "docs/architecture/overview.md", "docs/architecture/platform.md", "docs/architecture/constraints.md", "docs/architecture/components/workflow-artifacts.md", "docs/decisions/ADR-001-repository-native-template.md"]
expected_changes: "Create a coherent baseline, component/ADR context, navigation and clear example labels."
verification: ["Inspect specified acceptance outcomes and all local links; illustrative historical check only"]
documentation_impact: "create-new"
changeset:
  mode: "branch"
  branch: "ticket/T-001/task-001"
  base_branch: "main"
  base_commit: null
  commits: []
  files: ["docs/README.md", "docs/project.md", "docs/constitution.md", "docs/workflow.md", "docs/architecture/overview.md", "docs/architecture/platform.md", "docs/architecture/constraints.md", "docs/architecture/components/workflow-artifacts.md", "docs/decisions/ADR-001-repository-native-template.md"]
  external_pr: null
  review_state: "approved"
  exception: "Illustrative branch/snapshot only; no actual Git objects or executed historical review. Null base/commits are not available evidence for real acceptance."
```

## Task Dependencies

TASK-001 has no predecessors; stable order is TASK-001. The single changeset has no stacked dependency.

## Changeset Plan

One task per logical changeset. Branch names/bases above illustrate local operation only; they are not created. Null commits and EX-prefixed boundaries are explicitly teaching records, so a real reviewer must obtain actual immutable evidence before acceptance. No PR, push or merge is requested.

## Testing Strategy

Read changed docs against each acceptance outcome; inspect local link targets, metadata and example labels; compare guidance with reusable contracts. No application tests apply. In real work inspect actual working-tree changes, including untracked files, and use git diff --check when available. Sample progress does not claim this command was executed historically.

## Documentation Changes

Only the files named in task mappings; docs are the deliverable. Keep project index and current architecture consistent. No reusable instructions are changed by these ordinary sample tickets.

## Risks

A reader may mistake illustrative approval/history for real execution. Use example frontmatter and banners. Agent discovery is environment-dependent; explicit SKILL.md reading is the fallback. Source/commit evidence remains required for real review.

## Implementation Progress

Illustrative: TASK-001 pending -> ready -> in_progress -> implemented -> in_review -> accepted. Snapshot EX-T001-1 is a named teaching boundary for the listed paths, not an actual stored snapshot. R-001 records independent verification of AC-001/002/003 and completion. No historical command or real independent review is claimed.

## Iteration History

Illustrative iteration 1: specification revision 1, plan/contract revision 1; owner D-002 approves the baseline-only scope above. TASK-001 uses the illustrative branch and boundary recorded in its mapping. Independent R-001 approves the work and completion is recorded. No further iteration is needed; no real human decision, branch or review execution is claimed.
