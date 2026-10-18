---
name: ticket-implement
description: Execute the approved ticket iteration with minimal human interaction and record changes, verification, and review evidence.
---
# ticket-implement

Follow the [applicable role](../../roles/implementer.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use to execute the current approved iteration, including planned review fixes. Inputs: ticket ID and optional task ID. Read recorded decisions, boundaries and findings from the artifacts; the human need not repeat them in the prompt. Do not ask routine scope, priority or design questions: these belong in ticket-plan. Escalate only unforeseen conflicts, missing authorization or blockers that prevent safe execution; record the evidence and return affected work to planning.

## Context and Preconditions

Read specification, current iteration plan, review contract, relevant source and findings. Read [task/Git model](../../../.sdd/references/task-and-git-model.md) and [review policy](../../../.sdd/references/review-policy.md). Require aligned current revisions, applicable iteration approval, allowed paths and satisfied dependencies. After a review requests changes, require a new approved plan iteration addressing that run before implementing any corrections. Open findings mapped to approved correction tasks do not prevent those fixes; unresolved dependency blockers still prevent unrelated downstream work.

## Workflow

1. Select requested work from the current iteration or the first ready task in its dependency order. Execute only changes and finding actions already selected in that plan; do not triage review scope or choose which suggestions to implement here. If the latest changes-requested run is not covered by a new approved iteration, hand off to ticket-plan. If no task is ready, record blockers rather than skip predecessors. An approved evidence-only iteration records its prescribed checks and handoff without inventing edits.
2. Inspect working-tree changes and establish a real task changeset boundary before editing: base/branch/commits or documented working-tree scope. Branch/commit creation respects authorization. Preserve unrelated work and never create remote resources.
3. Move eligible states to in_progress and implement approved scope only. Each task is one logical reviewable changeset. Ordinary project work cannot edit .agents/ or .sdd/.
4. Add/update application tests when appropriate to the project/change. Inspect and run applicable checks; for documentation work inspect content, links and contracts without adding a harness. Record actual outcomes, failures and checks not run.
5. Include required documentation/ADR work. Scope or architecture conflicts return to planning/decision with evidence; never silently change criteria or accepted decisions.
6. Persist actual paths, boundaries, verification evidence and progress. Mark implemented only with complete required work and passing checks; failures remain explicit blockers. Continue other ready work within requested scope. Reruns reuse progress rather than reapply completed work.
7. For review fixes, append resolution proposals, actual verification results and the changed boundary to the finding history. Do not mark findings resolved or downgrade them; the independent reviewer verifies fixes. A wont_fix disposition requires an authorized human decision under review policy. Preserve prior attempts on reruns without duplicating tasks or findings.
8. When the iteration's required work is implemented, move the ticket to in_review and hand off exact revisions, boundary and unresolved concerns. The flow is spec once, then plan -> implement -> review -> plan -> implement -> review until the current boundary passes independent review and completion gates. Do not self-review or invoke another session without authorization.

## Outputs, Validation, and Completion

Scoped changes, updated docs and persisted progress/evidence. Inspect the final diff and contract coverage. Never accept your own tasks, issue independent approval, or mark tickets done. Missing review independence is a handoff condition, not a fabricated passing verdict.
