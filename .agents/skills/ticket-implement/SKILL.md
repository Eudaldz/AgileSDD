---
name: ticket-implement
description: Execute approved ready SDD tasks and record changeset evidence and required documentation updates.
---
# ticket-implement

Follow the [applicable role](../../roles/implementer.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use to implement a planned ticket or named task. Inputs: ticket ID and optional task ID.

## Context and Preconditions

Read specification, plan, review contract, relevant source and findings. Read [task/Git model](../../../.sdd/references/task-and-git-model.md). Require aligned current revisions, applicable approvals, allowed paths, satisfied dependencies and no unresolved blocking finding affecting the work.

## Workflow

1. Select requested ready work or the first ready task in stable dependency order. If none is ready, identify blockers rather than skip predecessors.
2. Inspect working-tree changes and establish a real task changeset boundary before editing: base/branch/commits or documented working-tree scope. Branch/commit creation respects authorization. Preserve unrelated work and never create remote resources.
3. Move eligible states to in_progress and implement approved scope only. Each task is one logical reviewable changeset. Ordinary project work cannot edit .agents/ or .sdd/.
4. Add/update application tests when appropriate to the project/change. Inspect and run applicable checks; for documentation work inspect content, links and contracts without adding a harness. Record actual outcomes, failures and checks not run.
5. Include required documentation/ADR work. Scope or architecture conflicts return to planning/decision with evidence; never silently change criteria or accepted decisions.
6. Persist actual paths, boundaries, verification evidence and progress. Mark implemented only with complete required work and passing checks; failures remain explicit blockers. Continue other ready work within requested scope. Reruns reuse progress rather than reapply completed work.
7. When all required tasks are implemented, move the ticket to in_review and hand off exact revisions, boundary and unresolved concerns.

## Outputs, Validation, and Completion

Scoped changes, updated docs and persisted progress/evidence. Inspect the final diff and contract coverage. Never accept your own tasks, issue independent approval, or mark tickets done. Missing review independence is a handoff condition, not a fabricated passing verdict.
