---
example: true
---
# Sprint and ticket examples

Every artifact here is illustrative teaching state. Approvals, reviewers, branch names, snapshots and historical checks are not real execution evidence and must not be inherited by an adopting project.

## Walkthrough

- [Sprint 001](sprints/sprint-001.md): documentation baseline, with unfinished research explicitly carried over.
- [T-001](T-001/specification.md): completed documentation ticket; [plan](T-001/implementation.md), [review contract](T-001/review.md), [findings](T-001/review-findings.md).
- [Sprint 002](sprints/sprint-002.md): adoption guidance and the same carried research ID.
- [T-002](T-002/specification.md): completed ticket with a two-task local stack; [plan](T-002/implementation.md), [contract](T-002/review.md), [finding/fix/re-review history](T-002/review-findings.md).
- [T-003](T-003/specification.md): draft research stub. No plan or review artifacts exist because it has not reached that stage.

## Conventions

Allocate ticket IDs repository-wide, independent of sprint number. Each ticket starts with specification.md only. Planning adds implementation.md and review.md; actual review adds review-findings.md. Tasks live inside the plan, not separate files. Specifications own metadata, manifests own membership, and review runs append findings/history.

Normal progression is draft -> specified -> planned -> in_progress -> in_review -> accepted -> done, with explicit blocked/cancelled states. Required approvals and completion rules are in the [lifecycle](../.sdd/references/lifecycle.md). Revisions preserve stable requirement/task IDs and completed work; carryover preserves ticket identity.

For real work follow [artifact contracts](../.sdd/references/artifact-contracts.md), [task/Git rules](../.sdd/references/task-and-git-model.md), and [review policy](../.sdd/references/review-policy.md). Never copy sample approvals, mark unreviewed work done, or discard existing project history during adoption.
