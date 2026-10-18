---
ticket_id: "{{T-nnn}}"
spec_revision: 1
plan_revision: 1
plan_status: draft
planned_on: "{{YYYY-MM-DD}}"
approval:
  state: pending
  by: null
  evidence: null
---
# Implementation: {{T-nnn}}

## Metadata

Frontmatter owns plan metadata; the specification owns ticket status.

## Specification Reference

{{link to specification and exact revision}}

## Existing Context

{{actual source, constitution, architecture, ADRs, and implemented/absent behavior}}

## Human Direction

{{this iteration's human priorities, constraints and tradeoff decisions; instructions or questions/answers; unresolved decisions prevent approval}}

## Iteration Scope

{{concrete Markdown description of what will change in this iteration, exclusions and expected outcomes; plan_revision is the iteration number}}

## Finding Assessment

| Finding | Validity and evidence | In scope? Why? | Proposed action and task |
|---|---|---|---|
| {{finding ID or no review yet}} | {{valid/disputed/invalid proposal and evidence}} | {{specification/project rule or optional enhancement}} | {{fix, evidence-only recheck, or authorized follow-up; reviewer owns resolution}} |

## Technical Approach

{{design, affected components, data/interfaces, external dependencies, migration, and material alternatives}}

## Architecture Impact

{{current/proposed changes and any decision required before implementation}}

## Acceptance Criteria

{{canonical criterion IDs and wording from the referenced specification revision, or exact links; do not redefine}}

## Ordered Tasks

### TASK-001

```yaml
id: TASK-001
title: "{{coherent task}}"
status: pending
depends_on: []
acceptance_criteria: [AC-001]
supporting_work: null
files: []
expected_changes: "{{files and intended change}}"
verification: ["{{applicable check and expected outcome}}"]
documentation_impact: update-existing
changeset:
  mode: branch
  branch: null
  base_branch: null
  base_commit: null
  commits: []
  files: []
  external_pr: null
  review_state: pending
  exception: null
```

Null Git fields mean not yet established; populate the actual boundary before implementation/review. Add further task mappings under new stable headings, not separate files.

## Task Dependencies

{{stable topological ordering, readiness gate, and any multi-parent base decision}}

## Changeset Plan

{{one task per changeset, intended local bases, working-tree fallback, and permission boundaries}}

## Testing Strategy

{{existing project checks/application tests when appropriate, manual checks, expected outcomes, and reasons for inapplicable checks}}

## Documentation Changes

{{affected current-state docs and ADRs; each task declares its impact}}

## Risks

{{uncertainties, security, migration, and unresolved decisions}}

## Implementation Progress

{{append actual evidence, exact commands/outcomes or manual observations, task status transitions, plan revisions, and limitations; never claim simulated checks were run}}

## Iteration History

{{before replacing an approved iteration, preserve its plan/contract revision, human direction, scope, decisions, approval evidence, task boundaries, review outcomes and next-iteration reason; retain completed work without duplicating editable task mappings}}
