---
name: ticket-reconcile
description: Address SDD review findings while preserving history and independent reviewer acceptance authority.
---
# ticket-reconcile

Follow the [applicable role](../../roles/implementer.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use to address findings after review. Inputs: ticket ID and optional selected findings.

## Context and Preconditions

Read specification, implementation/review contracts, all open findings and relevant diffs/files. Read [review policy](../../../.sdd/references/review-policy.md) and [task/Git model](../../../.sdd/references/task-and-git-model.md). Require real findings and identifiable scope; never synthesize a reviewer or run to justify fixes.

## Workflow

1. Map selected findings to an existing task, new task, plan/specification revision or docs update. Preserve original IDs, evidence, severity, run history and decisions.
2. Acknowledge with intended action. Reopen affected tasks for fixes within approved scope, following implementer constraints. Material scope/architecture changes require replanning and applicable approval before implementation.
3. Apply scoped fixes, include docs, rerun relevant checks and record actual results and changed boundary. Preserve unrelated changes and completed work.
4. Append resolution proposals and re-review needs. Implementer claims do not resolve findings; reviewer verification does. Wont_fix requires an authorized human decision, rationale and policy evidence.
5. Invalidate affected approvals if requirements changed. Repeated runs preserve prior attempts and avoid duplicate tasks/findings. Leave acceptance pending until independent review of the changed boundary.

## Outputs, Validation, and Completion

Task updates, authorized fixes, appended resolution evidence and exact re-review handoff. Check mapping and history preservation. Missing decisions block affected work only; never delete, silently downgrade, self-approve, automatically accept, or perform remote actions.
