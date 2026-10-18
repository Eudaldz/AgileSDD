---
example: true
ticket_id: "T-002"
spec_revision: 1
plan_revision: 1
plan_status: "approved"
planned_on: "2026-10-18"
approval:
  state: "approved"
  by: "Illustrative project owner"
  evidence: "Illustrative decision D-002: approve the specific specification and plan; not actual authorization"
---
# Implementation: T-002

> Illustrative example. Decisions, actors, branches, snapshots, and historical checks below are teaching records, not actual approvals, Git objects, or executed history.

## Metadata

Frontmatter identifies the illustrative plan approval. Specification owns ticket status.

## Specification Reference

[Specification](specification.md), revision 1; [review contract](review.md), contract revision 1.

## Existing Context

Read [constitution](../../docs/constitution.md), [overview](../../docs/architecture/overview.md), [workflow](../../docs/workflow.md), and [ADR-001](../../docs/decisions/ADR-001-repository-native-template.md). Only repository text is present; no application is inferred.

## Technical Approach

First provide the root adoption entry point, then expand it with preservation, rerun, revision and reviewer-handoff guidance. The documentation guide relies on the entry-point route and links back to the current baseline. No runtime dependencies, interfaces or migration are introduced.

## Architecture Impact

No runtime architecture change. The docs describe current file boundaries, with teaching history visibly illustrative. ADR-001 constrains scope; no additional decision or source migration is needed.

## Acceptance Criteria

Use the exact canonical AC IDs and wording from the [specification revision 1](specification.md). Task mappings below and the [review contract](review.md) cover every criterion without redefining it.

## Ordered Tasks

### TASK-001

```yaml
id: "TASK-001"
title: "Add the adoption entry point"
status: "accepted"
depends_on: []
acceptance_criteria: ["AC-001"]
supporting_work: null
files: ["README.md"]
expected_changes: "Explain copy/use/learn paths, skill invocation and file ownership."
verification: ["Inspect specified acceptance outcomes and all local links; illustrative historical check only"]
documentation_impact: "create-new"
changeset:
  mode: "branch"
  branch: "ticket/T-002/task-001"
  base_branch: "main"
  base_commit: null
  commits: []
  files: ["README.md"]
  external_pr: null
  review_state: "approved"
  exception: "Illustrative branch/snapshot only; no actual Git objects or executed historical review. Null base/commits are not available evidence for real acceptance."
```

### TASK-002

```yaml
id: "TASK-002"
title: "Document preservation and independent handoff"
status: "accepted"
depends_on: ["TASK-001"]
acceptance_criteria: ["AC-002", "AC-003"]
supporting_work: null
files: ["docs/development/adoption.md", "docs/README.md"]
expected_changes: "Expand the README entry path into an existing-project preservation guide and fresh-reviewer handoff; add guide navigation."
verification: ["Inspect specified acceptance outcomes and all local links; illustrative historical check only"]
documentation_impact: "update-existing"
changeset:
  mode: "branch"
  branch: "ticket/T-002/task-002"
  base_branch: "ticket/T-002/task-001"
  base_commit: null
  commits: []
  files: ["docs/development/adoption.md", "docs/README.md"]
  external_pr: null
  review_state: "approved"
  exception: "Illustrative branch/snapshot only; no actual Git objects or executed historical review. Null base/commits are not available evidence for real acceptance."
```

## Task Dependencies

Stable order TASK-001 then TASK-002. TASK-002 depends on the entry point that it expands, so it bases on task-001. The configured implemented predecessor gate allows progression before final ticket acceptance; no dependency is invented for scheduling convenience.

## Changeset Plan

One task per logical changeset. Branch names/bases above illustrate local operation only; they are not created. Null commits and EX-prefixed boundaries are explicitly teaching records, so a real reviewer must obtain actual immutable evidence before acceptance. No PR, push or merge is requested.

## Testing Strategy

Read changed docs against each acceptance outcome; inspect local link targets, metadata and example labels; compare guidance with reusable contracts. No application tests apply. In real work inspect actual working-tree changes, including untracked files, and use git diff --check when available. Sample progress does not claim this command was executed historically.

## Documentation Changes

Only the files named in task mappings; docs are the deliverable. Keep project index and current architecture consistent. No reusable instructions are changed by these ordinary sample tickets.

## Risks

A reader may mistake illustrative approval/history for real execution. Use example frontmatter and banners. Agent discovery is environment-dependent; explicit SKILL.md reading is the fallback. Source/commit evidence remains required for real review.

## Implementation Progress

Illustrative: TASK-001 progresses to accepted at R-001. TASK-002 progresses to in_review at EX-T002-2; R-002 opens F-001 and requests changes. Reconciliation acknowledges F-001, returns TASK-002 to in_progress and adds the explicit preservation rule at EX-T002-3. Rechecks are proposed, not self-approved. R-003 verifies the fix, resolves F-001, accepts TASK-002 and the full ticket, then records done. Spec/plan revision remain 1 because the fix restores existing AC-002; no scope or criteria changed.
