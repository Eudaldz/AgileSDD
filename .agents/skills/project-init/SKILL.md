---
name: project-init
description: Initialize or adopt SDD project documentation without creating sprints or tickets.
---
# project-init

Follow the [applicable role](../../roles/planner.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use for a new/existing repository or incomplete initialization. Inputs: location, optional product purpose, constraints, principles, and workflow overrides.

## Context and Preconditions

Read [documentation governance](../../../.sdd/references/documentation-governance.md). Inspect repository instructions, Git state, paths, README, existing docs, relevant source, manifests, tests, CI, and infrastructure. Exclude generated/vendor content. Classify as new, existing, or already initialized. Missing product facts are questions or explicitly unverified, never invented architecture.

## Workflow

1. Infer existing boundaries from actual files. For a new project use supplied purpose/constraints/conventions, asking only material missing facts. Mark future architecture proposed and uncertain architecture unverified.
2. Inspect existing docs/tickets before editing. Clearly labeled sample state can be replaced only when adoption replacement is authorized; never delete mixed or real ticket history. Preserve approved documentation and unrelated work on every rerun.
3. Use [project](../../../.sdd/templates/project.md), [constitution](../../../.sdd/templates/constitution.md), [workflow](../../../.sdd/templates/workflow.md), and [architecture](../../../.sdd/templates/architecture.md) templates to fill missing baseline documents. Create `docs/README.md` navigation and `tickets/README.md` conventions. Add component/ADR docs only for actual needs; decisions remain proposed until approved.
4. Inspect configuration, required headings, links, and evidence. Confirm no source or reusable-framework files changed. Propose evidence-backed updates for stale approved content instead of overwriting it.

## Outputs, Validation, and Completion

Baseline project documentation and a ticket guide; no ticket or sprint records. Report generated/preserved paths and actual checks. Collisions and missing material facts block affected writes only; retain uncertainty rather than claim completeness. Reruns fill gaps without duplicating content.
