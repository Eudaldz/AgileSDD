---
example: true
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
  verification_commands:
    whitespace: git diff --check
  allowed_implementation_paths: [README.md, docs/, tickets/]
---
# Project workflow

## Configuration

This example uses the reusable defaults with project-specific documentation paths and a Git whitespace check. Fields merge recursively according to the [artifact contracts](../.sdd/references/artifact-contracts.md). No configuration loader is needed. The `example` flag is artifact metadata, not an SDD option.

## Project Checks

Inspect UTF-8 Markdown, YAML fields, required headings, links, revisions, state gates, stable IDs, dependency order, and criterion mappings. Read actual files and check untracked files explicitly. Inspect commands before running them. No application test suite applies to this repository.

## Approvals and Review

A human developer approves specific scope/plan decisions; a fresh reviewer session or a human other than the implementer verifies actual changes. Reference actual messages/decisions in real work. Example approvals and reviews in tickets are illustrative only.

## Git Boundaries

`main` is an illustrative project base in sample changesets, not a claim about the current checkout. Branches described by sample tasks are not created. In real work inspect the actual base and obtain any necessary branch/commit authorization. A working-tree alternative requires `git.mode: working-tree`, stacked changesets false, exact paths, and an identifiable captured review snapshot.

## Policy Exceptions

None. Sample records do not waive actual approvals or independence. Maintenance of `.agents/` and `.sdd/` requires a separate explicit template-maintenance request; ordinary project tickets cannot grant that exception.
