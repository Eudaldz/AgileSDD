# Independent review and findings

## Contract and reviewer

A planner writes `review.md` alongside every iteration plan. It states the fixed specification revision, current plan revision, acceptance mapping, changeset boundaries, project verification commands or manual checks, architecture/ADR/security concerns, documentation checks, and reporting format. It also identifies prior findings to verify and evidence for disputed or out-of-scope findings. The implementer cannot weaken this contract to pass review. Material implementation decisions return to human-led planning; changed product requirements need a linked ticket, not a rewritten specification.

Use a fresh reviewer session or an authorized human who did not implement the work. A single session switching role labels is not independent review. Do not spawn agents unless delegation is authorized. If independence is unavailable, prepare the contract and report acceptance blocked; the implementer may record checks but cannot issue their own approval. A project waiver requires a recorded human decision and an acceptance authority other than the implementer.

Inspect actual files and diffs, including untracked content, rather than trusting summaries. Review only an identified snapshot/boundary. Record exact spec/plan revisions and the files/commits or snapshot reviewed. Verify every acceptance criterion, relevant behavior and regressions, architecture and ADR compliance, security boundaries, project checks, and documentation. Missing source/evidence, stale revisions, or an unstable boundary are blockers. Do not modify application implementation in a normal review.

## Runs and verdicts

Append a run with an immutable ticket-scoped `R-nnn`, reviewer identity, scope, boundary, checks and outcomes, limitations, and verdict: `approved`, `changes_requested`, or `blocked`. Each task has a review state, distinct from ticket state. Approve a full ticket only when required tasks are accepted, all criteria are verified, project checks pass, dependencies are satisfied, documentation is current, and no blocking findings remain. Approval does not merge, push, publish, or automatically mark done.

Default blocking severities are critical and major. Minor/suggestion findings need recorded follow-up or rationale before completion but need not block approval unless the project policy says otherwise. A blocker is a finding with unresolved evidence needed for a verdict, not a reason to invent a passing result.

Findings must distinguish violations of the approved specification, project rules or actual regressions from optional improvements. Human-led planning evaluates validity and ticket scope against evidence, not reviewer preference alone. A valid out-of-scope enhancement may be deferred to an authorized linked ticket; a verified acceptance failure cannot be excluded merely by calling it out of scope. A disputed blocker remains blocking until independently resolved or dispositioned under recorded policy. Planning records proposals and human priorities; it does not erase findings or grant itself a passing verdict.

## Finding lifecycle

Use the mapping in [artifact contracts](artifact-contracts.md). IDs remain stable across runs. States: `open`, `acknowledged`, `resolved`, `wont_fix`.

- `open -> acknowledged`: implementer records understanding, intended action, and affected tasks.
- `open/acknowledged -> resolved`: reviewer verifies a concrete fix or evidence that the reported defect is invalid against the current boundary, and appends the reason and evidence. Planner/implementer claims are proposals, not resolved findings.
- `open/acknowledged -> wont_fix`: explicit authorized human decision, rationale, and policy reference; reviewer records whether acceptance is permitted. Never downgrade severity simply to avoid a gate.
- Reopen a resolved/wont_fix finding when new evidence defeats its disposition, preserving prior history and adding a new run reference.

After changes_requested, use `ticket-plan` for the same ticket with human context about priorities, constraints and disputed findings. Record each finding's validity, scope, rationale and proposed action; select corrections, evidence-only rechecks or follow-up work without changing the fixed specification. Mark the prior plan needs_reconciliation and require a new approved iteration before fixes. Then use `ticket-implement` to execute that plan and `ticket-review` in an independent session to verify the result. Repeat plan -> implement -> review until review approves and completion gates pass. Preserve original evidence, severity, resolution attempts and prior runs. Never delete findings or old verdicts after a fix. Do not report invented independent reviewers, commands, commits, or results; teaching examples must be visibly illustrative.
