---
name: ticket-spec
description: Create or revise one SDD specification while preserving requirement IDs and completed-work history.
---
# ticket-spec

Follow the [applicable role](../../roles/planner.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use to refine a stub or revise requirements. Inputs: ticket ID and requested behavior. Create a new ticket only when explicitly requested within approved scope.

## Context and Preconditions

Read active specification, relevant architecture/ADRs/source, dependencies and existing downstream artifacts. Reject a missing or ambiguous ID rather than invent a target.

## Workflow

1. Compare requested behavior with actual implementation and prior specification. Establish problem, objective, scope/exclusions, constraints, assumptions, dependencies and open questions.
2. Use the [specification template](../../../.sdd/templates/specification.md). Give requirements stable FR/NFR IDs and acceptance criteria observable outcomes and verification methods. Research/design tickets may specify technical deliverables.
3. Preserve unchanged IDs and human decisions. Append new IDs; mark withdrawn requirements superseded. Increment substantive revisions and record affected implemented work and downstream impact.
4. Material changes invalidate affected approvals and mark the existing plan needs_reconciliation. Preserve completed tasks. Reopen a done ticket only on explicit instruction; prefer a linked successor for independent enhancements.
5. Resolve material questions before specified status. Check metadata, dependencies, acceptance coverage, links, constitution/ADR conflicts, and actual approval evidence. Apply lifecycle gates; never approve on behalf of the user.

## Outputs, Validation, and Completion

One updated specification and required downstream-staleness markers. Complete means clear, verifiable, revisioned, with applicable approvals. Otherwise leave an honest draft with blockers and next actions. Do not implement or rewrite accepted architecture to conceal a conflict.
