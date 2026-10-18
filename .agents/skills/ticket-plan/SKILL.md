---
name: ticket-plan
description: Create a dependency-aware implementation plan and independent review contract for one specified ticket.
---
# ticket-plan

Follow the [applicable role](../../roles/planner.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use for planning/replanning one ticket. Inputs: ticket ID and optional technical constraints.

## Context and Preconditions

Read specification, existing plan/review/findings and actual source. Read [task/Git model](../../../.sdd/references/task-and-git-model.md) and [review policy](../../../.sdd/references/review-policy.md). Final planning requires a specified ticket and required specification approval; unresolved requirements allow only a draft.

## Workflow

1. Establish actual baseline, spec revision, technical approach, affected components/interfaces/data, migration, external dependencies, alternatives and risks. Identify architecture decisions required before implementation.
2. Use the [implementation template](../../../.sdd/templates/implementation.md). Split work into coherent tasks, mapped to canonical criteria or justified supporting work. Name expected paths, changes, checks, documentation impact and local changeset boundaries. Never create per-task files.
3. Check unique IDs, dependency references/cycles, stable topological order and readiness gates. Independent tasks base on an appropriate project branch; dependent tasks may form a stack. Multiple predecessor branches require an explicit base/integration decision, not an automatic merge.
4. Use the [review template](../../../.sdd/templates/review.md) to map every criterion to repeatable independent checks, boundaries, architecture/security/documentation concerns, and applicable project checks. Give a fresh reviewer sufficient context; do not impose tests on documentation-only work or invent commands.
5. On revision preserve completed task IDs, changesets, evidence, findings and decisions. Append new work, cancel obsolete unstarted work and flag affected completed tasks. Increment plan/contract revisions and align specification references without redefining acceptance.
6. Inspect coverage, metadata, dependencies, links and boundaries. Obtain required approval only when not already supplied. Mark plan approved and ticket planned only when gates pass. Describing branches does not create them.

## Outputs, Validation, and Completion

One implementation.md and one review.md, usable in fresh sessions. Missing decisions/evidence/approvals leave draft or needs_reconciliation state with explicit blockers. Report readiness honestly; do not implement while planning.
