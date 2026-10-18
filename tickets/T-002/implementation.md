---
example: true
ticket_id: "T-002"
spec_revision: 1
plan_revision: 2
plan_status: "approved"
planned_on: "2026-10-18"
approval:
  state: "approved"
  by: "Illustrative project owner"
  evidence: "Illustrative decision D-003: approve iteration 2 to correct F-001 only; not actual authorization"
---
# Implementation: T-002

> Illustrative example. Decisions, actors, branches, snapshots, and historical checks below are teaching records, not actual approvals, Git objects, or executed history.

## Metadata

Frontmatter identifies the illustrative plan approval. Specification owns ticket status.

## Specification Reference

[Specification](specification.md), revision 1; [review contract](review.md), contract revision 2.

## Existing Context

Read [constitution](../../docs/constitution.md), [overview](../../docs/architecture/overview.md), [workflow](../../docs/workflow.md), and [ADR-001](../../docs/decisions/ADR-001-repository-native-template.md). Only repository text is present; no application is inferred.

## Human Direction

Illustrative iteration-2 owner context: preserving existing project state is essential. Correct the missing preservation rule reported in F-001; keep the accepted README entry point and current navigation. Do not broaden this into an installer or cross-agent discovery project. Discovery research remains T-003. The planner confirms that explicit preservation means existing docs, source, application tests and ticket history, as already required by AC-002. Illustrative D-003 approves these exact corrections; D-002 approved only the first iteration.

## Iteration Scope

Iteration 2 changes only the existing-project paragraph in docs/development/adoption.md through TASK-002, adding the missing preservation rule. Recheck links, AC-002 and the unchanged independent-handoff guidance under AC-003. No new feature, skill, task ID or specification change is proposed. TASK-001 stays accepted; docs/README.md remains part of TASK-002's original boundary but needs no new edit. TASK-002 is readied after D-003, implemented at EX-T002-3 and independently rechecked by R-003.

## Finding Assessment

| Finding | Validity and evidence | In scope? Why? | Proposed action and task |
|---|---|---|---|
| F-001 | Valid: R-002 identifies missing preservation language at EX-T002-2. | Yes: it directly violates existing AC-002. | Correct the paragraph in TASK-002, inspect the rule and links, then request independent verification; keep F-001 acknowledged until R-003. |

Cross-agent discovery is not a defect established by F-001 and is outside this correction. Its uncertainty remains visible in T-003; the planner does not invent a new finding or mark unrelated research complete.

## Technical Approach

Retain the first iteration's entry point and guide structure. Add explicit preservation language to the existing-project paragraph, restoring the fixed AC-002 without redesigning adoption. Use content and link inspection; no runtime dependencies, interfaces or migration are introduced.

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

Illustrative iteration 1: TASK-001 is accepted at R-001. TASK-002 reaches in_review at EX-T002-2; R-002 opens F-001 and requests changes, leaving the task unaccepted and marking the plan needs_reconciliation. The human and planner assess F-001 and approve iteration 2 as D-003. The ticket returns to planned, TASK-002 is readied, and implementation then moves it to in_progress, adds the preservation rule at EX-T002-3, records checks and proposes resolution. R-003 verifies the changed boundary under plan/contract revision 2, resolves F-001, accepts the full ticket and records completion. Specification revision remains 1; no requirement changed.

## Iteration History

### Iteration 1: initial adoption guide

- Specification revision 1; plan/contract revision 1. Illustrative owner D-002 approves a README entry point followed by a preservation and independent-handoff guide, with no installer, runtime or publishing work.
- Scope: TASK-001 changes README.md; TASK-002 changes docs/development/adoption.md and docs/README.md. Intended order and illustrative branch stack are retained in the task mappings. Checks are content, link and acceptance inspection; no application tests apply.
- Boundaries: EX-T002-1 for TASK-001, EX-T002-2 for TASK-002. R-001 approves TASK-001; R-002 finds F-001 and requests changes. The initial plan becomes needs_reconciliation. Its approval does not authorize a fix chosen by the implementer.

### Iteration 2: focused preservation correction

- Specification revision 1; plan/contract revision 2. Human direction, finding assessment and exact correction scope are recorded above. Illustrative D-003 approves only the F-001 correction and verification, preserving TASK-001 and excluding T-003 discovery research.
- Boundary: EX-T002-3 plus unchanged EX-T002-1. R-003 independently verifies the fix, resolves F-001 and approves the full ticket. Earlier runs remain attached to revision 1. All decisions, checks and snapshots are teaching records, not executed history.
