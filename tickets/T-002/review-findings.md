---
example: true
ticket_id: "T-002"
---
# Review findings: T-002

> Illustrative example. Decisions, actors, branches, snapshots, and historical checks below are teaching records, not actual approvals, Git objects, or executed history.

## Review Run History

### R-001

Illustrative Review Session B, independent of Implementer B: TASK-001, spec/plan revision 1, EX-T002-1 (README.md). AC-001 passes content/path inspection. Task-only verdict approved; this does not approve the full ticket.

### R-002

Same illustrative reviewer: TASK-002, spec/plan revision 1, EX-T002-2 (guide/index). AC-003 handoff is present; AC-002 lacks the preservation rule. Open F-001, verdict changes_requested; TASK-002 remains unaccepted and the plan becomes needs_reconciliation. Human-led planning follows before any fix: D-003 approves plan/contract revision 2, keeps the specification fixed, selects the AC-002 correction and excludes unrelated T-003 research.

### R-003

Same illustrative independent reviewer: TASK-002 re-review and full ticket, specification revision 1 and plan/contract revision 2, EX-T002-3 plus unchanged EX-T002-1. Corrected preservation paragraph satisfies AC-002; all mappings, docs and T-001 dependency checked. Resolve F-001, accept TASK-002, full verdict approved. All runs are teaching history, not actually executed checks or real snapshots.

## Review Verdict

Illustrative latest R-003: approved. R-002 remains changes_requested in history; R-001 was only task-scoped. No actual approval is implied.

## Findings

### F-001

```yaml
id: "F-001"
task_id: "TASK-002"
severity: "major"
category: "documentation-preservation"
description: "The first illustrative adoption-guide draft omits the explicit rule to preserve existing project state."
evidence: "At illustrative EX-T002-2, the existing-project paragraph says copy the reusable directories but does not explicitly retain approved docs/source/tests/ticket history, violating AC-002."
files: ["docs/development/adoption.md"]
suggested_resolution: "State that existing documentation, source, application tests and ticket history must be preserved; limit replacement to clearly labeled sample content with authorization."
status: "resolved"
introduced_in: "R-002"
resolution: "Illustrative R-003 checks the corrected preservation paragraph at EX-T002-3 and confirms AC-002. This is not actual execution evidence."
history: [{"run": "R-002", "actor": "Illustrative Review Session B", "action": "opened", "evidence": "EX-T002-2 omitted explicit preservation rule."}, {"run": "R-002", "actor": "Illustrative Implementer B", "action": "acknowledged", "evidence": "After human-led assessment, illustrative D-003 approves iteration 2 to reopen TASK-002 for explicit preservation language; specification revision 1 stays fixed."}, {"run": "R-003", "actor": "Illustrative Implementer B", "action": "proposed-resolution", "evidence": "EX-T002-3 adds preservation rule; request independent re-review."}, {"run": "R-003", "actor": "Illustrative Review Session B", "action": "resolved", "evidence": "Independently inspect corrected paragraph and full AC mapping in teaching sequence."}]
```

## Blocking Concerns

None remain in the illustrative final state. F-001 was major and blocked full acceptance until R-003; its original evidence and severity are retained.

## Non-Blocking Concerns

None recorded. Agent-discovery behavior outside explicit file reading remains unverified and separately scoped in T-003.

## Validation Evidence

Illustrative content/path/criterion checks only, with named teaching boundaries. No actual Git objects, command runs or independent session are asserted. Current files contain the final paragraph; historical drafts are described, not delivered as fake commits.

## Required Follow-Up

In actual work obtain a fresh reviewer and real immutable review boundary before acceptance. The teaching sequence has no remaining fix.

## Resolution History

Human-led planning assessed F-001 as valid and in scope under AC-002, mapped it to existing TASK-002, and approved iteration 2 as D-003 without changing requirements. Implementation then corrected it and proposed resolution; independent R-003 verified plan/contract revision 2 before resolving. Prior runs and history remain. Reviewer then recorded accepted -> done after documentation synchronization.
