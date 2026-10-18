---
ticket_id: "{{T-nnn}}"
spec_revision: 1
plan_revision: 1
contract_revision: 1
---
# Review contract: {{T-nnn}}

## Metadata

Frontmatter identifies the exact specification and plan this contract verifies.

## Review Scope

{{tasks, behavior, reviewer independence, and context for a fresh session}}

{{current iteration's prior-finding actions and disputed/out-of-scope proposals to independently verify; fixed specification remains the acceptance contract}}

## Specification Reference

{{links to specification, plan, constitution, relevant architecture, and ADRs}}

## Changeset Boundaries

{{task-to-base/branch/commits or explicit working-tree snapshot; inspect actual files including untracked content}}

## Acceptance Criteria Verification

| Criterion | Task | Independent check and expected result |
|---|---|---|
| AC-001 | TASK-001 | {{repeatable evidence and expected outcome}} |

## Functional Review

{{intended behavior, regressions, edge cases, and dependencies}}

## Architecture Review

{{constraints, ADR compliance, and current/proposed distinction}}

## Security Review

{{scope-relevant trust boundaries and sensitive-data checks}}

## Testing Verification

{{independently repeat applicable project checks; explain when application tests are inapplicable}}

## Documentation Verification

{{accuracy, links, required updates, and synchronization}}

## Review Commands

{{inspected literal Git/project commands or manual steps, expected outcomes, required tools, and unavailable-check handling}}

## Expected Reporting Format

Append runs and stable findings to `review-findings.md` using its template and `.sdd/references/review-policy.md`. Record actual reviewer, boundary, outcomes, limitations, and verdict. Missing evidence blocks approval. Do not edit implementation or approve your own work.
