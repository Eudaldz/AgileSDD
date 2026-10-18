---
name: sdd-sprint
description: Plan one bounded sprint after reconciliation and create approved ticket stubs.
---
# sdd-sprint

Follow the [applicable role](../../roles/planner.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use to prepare/revise one sprint. Inputs: goal, priorities, optional dates/capacity/scale, carryover, external references. Do not plan an unsolicited full-product roadmap.

## Context and Preconditions

Read [documentation governance](../../../.sdd/references/documentation-governance.md). Inspect previous sprint, open specifications, incomplete tasks, unresolved findings, relevant current source/checks, architecture and accepted ADRs. Missing baseline documentation requires initialization before finalizing.

## Workflow

1. Reconcile before proposing work: distinguish implemented, planned, partial, defect, drift, and unknown observations. Record evidence, severity, affected paths, proposed action, owner/ticket and confidence in the sprint reconciliation section.
2. Propose bounded, dependency-aware work using all supported ticket types. Story points apply to whole-ticket relative effort and uncertainty, not time guarantees. Respect capacity when supplied.
3. Prepare a [sprint manifest](../../../.sdd/templates/sprint.md) with goal, optional dates/capacity, risks, acceptance conditions, proposed membership and carryover. Let the human revise the concrete proposal; existing authorization satisfies approval only when it covers that scope. Otherwise leave proposed and create no ticket directories.
4. After approval recheck ID allocation and create only [specification](../../../.sdd/templates/specification.md) stubs with draft status. Mark unresolved sections honestly; do not produce every ticket's plan/review artifacts.
5. Reuse IDs/history for carryover. Record source/destination membership changes, deferrals, splits, cancellations, and rationale. A ticket cannot belong to two active sprints. Specifications own status/priority/estimate; avoid copied editable values in sprint tables.

## Outputs, Validation, and Completion

A manifest with reconciliation and actual approval state; approved scope has draft ticket stubs. Check configuration, unique IDs, links, dependencies, membership, capacity and allowed paths. Reruns reuse selected artifacts rather than allocate duplicates. Missing decisions leave a concrete pending proposal, never fabricated activation.
