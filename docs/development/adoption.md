---
example: true
---
# Adoption and daily use

## Replace sample state safely

In a new copy, replace sample project documentation and ticket history with your product's actual context before planning real work. The examples are marked `example: true`; remove that flag from newly authored real records. Do not inherit sample approvals or completed states. Keep `.agents/` and `.sdd/` unchanged.

For an existing project copy only the reusable directories initially. Inspect collisions if it already has SDD files. Ask the agent to use `project-init` to add missing project knowledge without overwriting approved documentation, source, tests or ticket history. Review stale-document proposals. The same procedure applies to Python, TypeScript and documentation-only repositories; initialization inspects the actual project rather than imposing a stack.

## Initialize and rerun

Supply purpose, known constraints and engineering practices. Baseline docs describe what exists; future behavior is proposed and uncertain conclusions are unverified. Initialization creates a ticket guide, not sprints/tickets. Repeating initialization fills missing docs and proposes stale-content updates; it does not reset history.

## Specify once and plan each iteration

Supply a sprint outcome, priorities, exclusions and capacity. Reconcile actual implementation and open work before approving a bounded sprint. Refine each selected stub into one human-owned specification with behavior examples, scope and success criteria. Ask and answer the product questions needed before approval; after approval, requirements and acceptance criteria stay fixed. Lifecycle metadata and factual history remain writable. Changed product requirements need a separately authorized linked ticket.

Before every implementation iteration, use ticket-plan with human engineering direction and constraints. Supply written instructions or ask the agent to interview you until priorities, compatibility and tradeoffs are settled. After review, add context about what matters, what does not and which findings you dispute. The planner checks actual evidence, classifies validity and scope, and proposes corrections or follow-up without changing the specification. A valid acceptance failure cannot be excluded merely because it is inconvenient.

The Markdown plan states exactly what this iteration will change, exclusions, task boundaries, checks and review expectations. plan_revision is the iteration number. Preserve earlier scope, human decisions, approval evidence and outcomes in Iteration History before replacing the current narrative. Keep task identities and completed work. Approve the actual next iteration; prior approval covers only its original scope unless explicit authorization already covers the new decisions.

## Implement and review with minimal interaction

Supply the ticket reference to ticket-implement. It executes the current approved iteration and records actual paths, base/commits or captured snapshot, checks, documentation updates and limitations. It does not choose which raw review suggestions to implement. Do not create a test harness for a documentation-only change; application work uses the project's appropriate checks.

Use ticket-review in a fresh independent session with the same ticket reference; it reads the recorded review contract and boundary. Implementation and review should almost never ask routine questions: decisions belong in the specification and plan. Unforeseen conflicts, missing authority or an inaccessible boundary are escalation exceptions. Record the blocker and return affected work to planning rather than guessing. Without an independent reviewer leave acceptance pending.

## Return review outcomes to planning

The flow is spec once, then plan -> implement -> review -> plan -> implement -> review until independent review approves and completion gates pass. A changes_requested verdict makes the prior plan needs_reconciliation; no direct fix cycle is allowed. Human-led planning assesses every finding, records rationale and selects fixes, evidence-only rechecks or authorized follow-up work. Optional improvements may be deferred; unresolved valid blockers still block acceptance.

Implementation follows the new approved iteration and proposes resolutions with evidence. The independent reviewer verifies fixes or disputed-finding evidence before resolving findings. Preserve all prior plans, runs, severities and attempted resolutions. Carry unfinished tickets between sprints with the same ID and explicit source/destination records.

## Git and permissions

Inspect the actual working tree first, including untracked files. Planned branch names do not create branches or authorize commits. Preserve unrelated changes. Multiple predecessor branches need a reviewed base decision; never automatically merge to make a stack work. Working-tree mode needs a captured identifiable review boundary; if unavailable, review is blocked. No skill publishes, pushes, or creates remote PRs.

## Walk the sample

[T-001](../../tickets/T-001/specification.md) establishes current project docs. [T-002](../../tickets/T-002/implementation.md) adds these adoption instructions after an entry-point task; its [review history](../../tickets/T-002/review-findings.md) demonstrates a missing preservation rule and re-review. [T-003](../../tickets/T-003/specification.md) stays draft across sprint carryover. These histories are illustrative; reading them is a walkthrough, not evidence that historical commands or reviews ran.
