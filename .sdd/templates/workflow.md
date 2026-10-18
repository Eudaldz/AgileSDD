---
sdd:
  story_points: [1, 2, 3, 5, 8, 13]
  default_sprint_length_days: 14
  require_spec_approval: true
  require_plan_approval: true
  require_independent_review: true
  require_docs_validation: true
  git:
    mode: local
    stacked_changesets: true
  validation:
    fail_on_broken_links: true
    require_acceptance_traceability: true
  task_ready_after: implemented
  verification_commands: {}
  allowed_implementation_paths: []
---
# Project workflow

## Configuration

Missing fields inherit `.sdd/defaults.yaml`; see `.sdd/references/artifact-contracts.md` for types and merge rules. Replace the empty command/path mappings only with actual project tools and authorized paths. Commands must be inspected before execution.

## Project Checks

{{manual checks and/or existing application checks; do not add a framework test runner}}

## Approvals and Review

{{who approves specifications/plans and independently accepts work; how decisions are referenced}}

## Git Boundaries

{{base branch and permission to create branches/commits, or a working-tree snapshot procedure}}

## Policy Exceptions

None unless an actual human decision is recorded with scope, authority, and rationale.
