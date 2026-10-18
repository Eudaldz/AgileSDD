# Lifecycle and revision rules

Read [artifact contracts](artifact-contracts.md) before mutation. Record each transition in the specification's `Change History`: previous/new state, reason, actor, and evidence. Update only the authoritative status; sprint membership contains no copied ticket status.

| Transition | Preconditions |
|---|---|
| draft -> specified | Scope, stable requirements, acceptance criteria, dependencies, and material questions resolved; specification approval recorded if required |
| specified -> planned | Plan and review contract match the current specification; tasks cover acceptance; dependency checks pass; required plan approval recorded |
| planned -> in_progress | Approved current plan; task dependencies and working-tree boundary checked |
| in_progress -> in_review | Current iteration's required work implemented; actual verification evidence and documentation changes recorded |
| in_review -> planned | Human-led ticket-plan assesses findings and approves a new iteration, preserving the prior plan, findings and verdicts |
| in_review -> accepted | Independent reviewer approves all required tasks and full ticket; all criteria verified; blocking findings resolved or explicitly dispositioned under policy |
| accepted -> done | Documentation synchronized; no unresolved required work; completion recorded by reviewer or human, never implementer alone |

`blocked` may interrupt any active state: retain the previous state and the blocker, owner, and unblock condition in history. Resume only that prior state after rechecking its preconditions. `cancelled` retains all records and rationale; restoration requires an explicit decision and rechecking the target-state gates. Never erase a partially completed plan.

The specification is drafted and approved once per ticket. Drafting may include several human conversations; after approval its requirements, scope and acceptance criteria stay fixed. Lifecycle metadata and factual history remain writable. Changed product requirements require a separately authorized linked ticket; do not rewrite the original specification to fit implementation or review. An unforeseen contradiction blocks affected work for human-led planning and a decision about a linked ticket.

The execution flow is spec once, then plan -> implement -> review -> plan -> implement -> review until accepted. Every iteration has its own human-led Markdown plan; plan_revision is the iteration number. After changes_requested, set plan_status needs_reconciliation and retain in_review until the next iteration is approved. There is no direct in_review -> in_progress correction path. The new plan records human direction, finding validity/scope decisions and exact corrections; implementation must not substitute its own triage.

Before updating an approved plan, preserve its scope, decisions, approval evidence, changeset boundaries and outcomes in Iteration History. Increment plan revision, preserve task IDs, cancel obsolete unstarted work, append newly identified work, and identify completed work affected by the change. Reopen only selected correction tasks, not all completed work. Reissue the review contract and obtain applicable approval for the new iteration before resuming. Approval of the prior iteration does not approve new work; existing authorization counts only when it covers the actual next-iteration decisions. Never reset completed work to pending just to make a new plan look clean.

Task states: `pending`, `ready`, `in_progress`, `implemented`, `in_review`, `accepted`, `blocked`, `cancelled`. Ready means dependency checks and the configured predecessor-state gate pass. Implemented means work and required evidence exist; only the reviewer/authorized human can accept. Findings leave affected tasks unaccepted; the next approved plan selects correction tasks and readies them after checking dependencies. Implementation then moves those tasks to in_progress; re-review follows a new run. A task can be blocked from any nonfinal state with its resume state recorded. Cancellation never implies predecessor completion. Record a replacement dependency explicitly rather than ignoring a cancelled predecessor.

Sprint states: `proposed`, `active`, `closed`. Only activate after the sprint decision is covered by human authorization. Closed sprints retain their committed membership; moving unfinished tickets creates a carryover record in both sprints. Active/proposed membership lists the current destination; a closed source list remains historical, not a second active assignment. A ticket may have at most one active sprint. Record additions, deferrals, splits, cancellations, and estimate changes with reasons; create successor tickets instead of losing original history.
