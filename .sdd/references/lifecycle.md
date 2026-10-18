# Lifecycle and revision rules

Read [artifact contracts](artifact-contracts.md) before mutation. Record each transition in the specification's `Change History`: previous/new state, reason, actor, and evidence. Update only the authoritative status; sprint membership contains no copied ticket status.

| Transition | Preconditions |
|---|---|
| draft -> specified | Scope, stable requirements, acceptance criteria, dependencies, and material questions resolved; specification approval recorded if required |
| specified -> planned | Plan and review contract match the current specification; tasks cover acceptance; dependency checks pass; required plan approval recorded |
| planned -> in_progress | Approved current plan; task dependencies and working-tree boundary checked |
| in_progress -> in_review | Required tasks implemented; actual verification evidence and documentation changes recorded |
| in_review -> accepted | Independent reviewer approves all required tasks and full ticket; all criteria verified; blocking findings resolved or explicitly dispositioned under policy |
| accepted -> done | Documentation synchronized; no unresolved required work; completion recorded by reviewer or human, never implementer alone |

`blocked` may interrupt any active state: retain the previous state and the blocker, owner, and unblock condition in history. Resume only that prior state after rechecking its preconditions. `cancelled` retains all records and rationale; restoration requires an explicit decision and rechecking the target-state gates. Never erase a partially completed plan.

On material requirement changes increment specification revision, preserve unchanged IDs, append new IDs, and mark withdrawn requirements as superseded with rationale. Invalidate both specification approval and downstream plan approval for the affected scope; set `plan_status: needs_reconciliation`. Return a planned ticket to specified only once the revised specification meets its gate; otherwise use draft. New review runs must name new revisions; old verdicts remain historical. A completed ticket reopens only on explicit instruction; prefer a linked successor for a separate enhancement.

Plan revisions preserve completed tasks, changesets, findings, and human decisions. Increment plan revision, preserve unchanged task IDs, cancel obsolete unstarted work, append newly identified work, and identify completed work affected by the change. Reissue the review contract and obtain applicable approval before resuming. Never reset completed work to pending just to make a new plan look clean.

Task states: `pending`, `ready`, `in_progress`, `implemented`, `in_review`, `accepted`, `blocked`, `cancelled`. Ready means dependency checks and the configured predecessor-state gate pass. Implemented means work and required evidence exist; only the reviewer/authorized human can accept. Findings return affected tasks to in_progress; re-review follows a new run. A task can be blocked from any nonfinal state with its resume state recorded. Cancellation never implies predecessor completion. Record a replacement dependency explicitly rather than ignoring a cancelled predecessor.

Sprint states: `proposed`, `active`, `closed`. Only activate after the sprint decision is covered by human authorization. Closed sprints retain their committed membership; moving unfinished tickets creates a carryover record in both sprints. Active/proposed membership lists the current destination; a closed source list remains historical, not a second active assignment. A ticket may have at most one active sprint. Record additions, deferrals, splits, cancellations, and estimate changes with reasons; create successor tickets instead of losing original history.
