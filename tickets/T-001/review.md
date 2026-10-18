---
example: true
ticket_id: "T-001"
spec_revision: 1
plan_revision: 1
contract_revision: 1
---
# Review contract: T-001

> Illustrative example. Decisions, actors, branches, snapshots, and historical checks below are teaching records, not actual approvals, Git objects, or executed history.

## Metadata

Contract revision 1 checks specification/plan revision 1; examples confer no actual approval.

## Review Scope

Independent review of all required tasks and full-ticket acceptance. A fresh session or independent human must inspect actual changes; the implementer cannot perform this acceptance.

## Specification Reference

[Specification](specification.md), [plan](implementation.md), [constitution](../../docs/constitution.md), [architecture](../../docs/architecture/overview.md), [ADR-001](../../docs/decisions/ADR-001-repository-native-template.md).

## Changeset Boundaries

TASK-001: listed documentation files, illustrative main -> ticket/T-001/task-001, EX-T001-1. These EX labels are illustrative, not actual captured snapshots or Git objects. Real review blocks until actual boundaries are supplied.

## Acceptance Criteria Verification

| Criterion | Task | Independent check and expected result |
|---|---|---|
| AC-001 | TASK-001 | Inspect baseline docs for current file evidence and absence of invented runtime. |
| AC-002 | TASK-001 | Follow documentation index targets, including ADR and component. |
| AC-003 | TASK-001 | Check example frontmatter and teaching-history labels. |

## Functional Review

Check each mapped outcome, local navigation, dependency satisfaction and preservation behavior. Verify the changed content itself instead of trusting progress summaries.

## Architecture Review

Check file ownership, no executable tooling, no runtime claims and ADR-001 compliance. Keep sample history separate from current file evidence.

## Security Review

Ensure guidance cannot override allowed paths or authorize arbitrary shell/network mutations. No credentials in artifacts and no destructive defaults.

## Testing Verification

No application test suite applies. Independently inspect content, headings, links, frontmatter, mapping coverage and actual diff boundaries; report unavailable checks.

## Documentation Verification

Follow links relative to each source; ensure the index describes present content and illustrative labels are retained. Required docs are part of the task deliverable.

## Review Commands

Manual: open every task path, compare each criterion, follow local links, and inspect actual boundary including untracked files. With Git, inspect status and task-only diffs using verified literal refs/paths, then git diff --check. No historical execution is claimed here; unavailable tools or missing immutable evidence block real approval.

## Expected Reporting Format

Append reviewer run ID, reviewer identity/independence, exact spec/plan revision, boundary, checks/outcomes/limitations, verdict and stable findings in [review-findings.md](review-findings.md). Preserve every run. Critical/major findings block until verified resolved or explicitly dispositioned under policy. Accept full ticket only after all tasks/criteria/docs/dependencies pass; no remote actions or self-approval.
