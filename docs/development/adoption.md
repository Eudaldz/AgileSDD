---
example: true
---
# Adoption and daily use

## Replace sample state safely

In a new copy, replace sample project documentation and ticket history with your product's actual context before planning real work. The examples are marked `example: true`; remove that flag from newly authored real records. Do not inherit sample approvals or completed states. Keep `.agents/` and `.sdd/` unchanged.

For an existing project copy only the reusable directories initially. Inspect collisions if it already has SDD files. Ask the agent to use `sdd-init` to add missing project knowledge without overwriting approved documentation, source, tests or ticket history. Review stale-document proposals. The same procedure applies to Python, TypeScript and documentation-only repositories; initialization inspects the actual project rather than imposing a stack.

## Initialize and rerun

Supply purpose, known constraints and engineering practices. Baseline docs describe what exists; future behavior is proposed and uncertain conclusions are unverified. Initialization creates a ticket guide, not sprints/tickets. Repeating initialization fills missing docs and proposes stale-content updates; it does not reset history.

## Plan bounded work

Ask for one sprint goal. The planner reconciles actual implementation, prior sprint outcomes, incomplete tasks and unresolved findings before proposing work. Approve the concrete scope, then refine a selected stub with ticket-spec and ticket-plan. Specifications own requirement IDs and ticket estimates; tasks map acceptance to changesets and include independent review instructions.

## Implement and hand off

Implement ready tasks against the current approved plan. Record actual paths, base/commits or captured snapshot, checks, documentation updates and limitations. Do not create a test harness for a documentation-only change. Application work uses the project's appropriate tests/checks.

Start a fresh reviewer session, supply the ticket ID and actual boundary, and ask it to use ticket-review. Without an independent reviewer, leave acceptance pending. Do not reinterpret an implementer summary as a review. Work can be implemented without being accepted.

## Revise and reconcile

A material requirement change increments specification revision, preserves IDs, invalidates affected approval and marks downstream planning stale. Replan while retaining completed tasks and history. Use a new linked ticket for an independent enhancement rather than silently reopening done work.

For findings, acknowledge and map each to scoped fixes or revised contracts. Append evidence after correction. A reviewer verifies the new boundary before resolving findings and accepting work. Keep every prior run and attempted resolution. Carry unfinished tickets between sprints with the same ID and explicit source/destination records.

## Git and permissions

Inspect the actual working tree first, including untracked files. Planned branch names do not create branches or authorize commits. Preserve unrelated changes. Multiple predecessor branches need a reviewed base decision; never automatically merge to make a stack work. Working-tree mode needs a captured identifiable review boundary; if unavailable, review is blocked. No skill publishes, pushes, or creates remote PRs.

## Walk the sample

[T-001](../../tickets/T-001/specification.md) establishes current project docs. [T-002](../../tickets/T-002/implementation.md) adds these adoption instructions after an entry-point task; its [review history](../../tickets/T-002/review-findings.md) demonstrates a missing preservation rule and re-review. [T-003](../../tickets/T-003/specification.md) stays draft across sprint carryover. These histories are illustrative; reading them is a walkthrough, not evidence that historical commands or reviews ran.
