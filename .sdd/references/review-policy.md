# Independent review and findings

## Contract and reviewer

A planner writes `review.md` alongside the plan. It states the exact specification/plan revision, acceptance mapping, changeset boundaries, project verification commands or manual checks, architecture/ADR/security concerns, documentation checks, and reporting format. The implementer cannot weaken this contract to pass review. Material changes go through specification/planning reconciliation.

Use a fresh reviewer session or an authorized human who did not implement the work. A single session switching role labels is not independent review. Do not spawn agents unless delegation is authorized. If independence is unavailable, prepare the contract and report acceptance blocked; the implementer may record checks but cannot issue their own approval. A project waiver requires a recorded human decision and an acceptance authority other than the implementer.

Inspect actual files and diffs, including untracked content, rather than trusting summaries. Review only an identified snapshot/boundary. Record exact spec/plan revisions and the files/commits or snapshot reviewed. Verify every acceptance criterion, relevant behavior and regressions, architecture and ADR compliance, security boundaries, project checks, and documentation. Missing source/evidence, stale revisions, or an unstable boundary are blockers. Do not modify application implementation in a normal review.

## Runs and verdicts

Append a run with an immutable ticket-scoped `R-nnn`, reviewer identity, scope, boundary, checks and outcomes, limitations, and verdict: `approved`, `changes_requested`, or `blocked`. Each task has a review state, distinct from ticket state. Approve a full ticket only when required tasks are accepted, all criteria are verified, project checks pass, dependencies are satisfied, documentation is current, and no blocking findings remain. Approval does not merge, push, publish, or automatically mark done.

Default blocking severities are critical and major. Minor/suggestion findings need recorded follow-up or rationale before completion but need not block approval unless the project policy says otherwise. A blocker is a finding with unresolved evidence needed for a verdict, not a reason to invent a passing result.

## Finding lifecycle

Use the mapping in [artifact contracts](artifact-contracts.md). IDs remain stable across runs. States: `open`, `acknowledged`, `resolved`, `wont_fix`.

- `open -> acknowledged`: implementer records understanding, intended action, and affected tasks.
- `open/acknowledged -> resolved`: reviewer verifies a concrete fix against the current boundary and appends evidence. An implementer's claimed fix is a resolution proposal, not a resolved finding.
- `open/acknowledged -> wont_fix`: explicit authorized human decision, rationale, and policy reference; reviewer records whether acceptance is permitted. Never downgrade severity simply to avoid a gate.
- Reopen a resolved/wont_fix finding when new evidence defeats its disposition, preserving prior history and adding a new run reference.

Reconciliation maps findings to an existing task, a new task, a revised plan/specification, or documentation. Preserve original evidence, append resolution attempts, rerun applicable checks, and identify which tasks require re-review. If findings change implementation scope or criteria, invalidate downstream approvals per [lifecycle](lifecycle.md). Never delete findings or old verdicts after a fix. Do not report invented independent reviewers, commands, commits, or results; teaching examples must be visibly illustrative.
