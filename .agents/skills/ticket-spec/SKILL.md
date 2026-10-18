---
name: ticket-spec
description: Structure human requirements into a ticket specification, finalized once before iterative planning begins.
---
# ticket-spec

Follow the [applicable role](../../roles/planner.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use to refine a stub into the ticket's one stable specification. Inputs: ticket ID and human-owned product intent, behavior, scope, constraints and acceptance examples, supplied directly or through recorded decisions. Drafting may involve several conversations; once approved, do not rewrite requirements during implementation iterations. Create a new ticket only when explicitly requested within approved scope.

## Context and Preconditions

Read active specification, relevant architecture/ADRs/source, dependencies and existing downstream artifacts. Reject a missing or ambiguous ID rather than invent a target.

## Workflow

1. Compare human-supplied behavior and decisions with actual implementation and prior specification. Structure the problem, objective, scope/exclusions, constraints, assumptions, dependencies and open questions. Humans are responsible for what the specification requires; help uncover missing details and propose options, but never silently decide material behavior or expand scope. Leave unanswered decisions explicit and ask focused questions with concrete examples or tradeoffs before finalizing.
2. Use the [specification template](../../../.sdd/templates/specification.md). Give requirements stable FR/NFR IDs and acceptance criteria observable outcomes and verification methods. Research/design tickets may specify technical deliverables.
3. While drafting, preserve requirement IDs and human decisions; append new IDs and retain a history of changes. Ask enough concrete questions to establish intended behavior, edge cases and exclusions rather than filling gaps with invented requirements.
4. After approval, keep requirements, scope and acceptance criteria fixed. A rerun reports the existing contract and directs iteration work to ticket-plan; changed requirements need a separately authorized linked ticket, not a rewritten contract for this ticket. Lifecycle metadata and factual history may still be updated without changing the approved requirements.
5. Resolve material questions before specified status. Check metadata, dependencies, acceptance coverage, links, constitution/ADR conflicts, and actual approval evidence. Apply lifecycle gates; never approve on behalf of the user.

## Outputs, Validation, and Completion

One human-reviewed specification, finalized once for this ticket. Complete means clear, verifiable, with applicable approval. Otherwise leave an honest draft with blockers and next questions. Do not implement or rewrite accepted requirements or architecture to conceal a conflict.
