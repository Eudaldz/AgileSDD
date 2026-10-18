---
example: true
---
# Technical constraints

## Status and Evidence

Current template constraints, reflected in [artifact contracts](../../.sdd/references/artifact-contracts.md) and [constitution](../constitution.md).

## Responsibilities and Boundaries

Skills guide agents; templates define artifacts; project state stays in docs/tickets. Application edits require explicit approved task paths. No normal skill can redefine framework policy.

## Structure and Data Flow

One specification owns ticket metadata. One plan owns its task mappings. Review runs append evidence and preserve prior verdicts. Sprint membership is authoritative in frontmatter, with closed-sprint commitments retained as history.

## Platform and Dependencies

No CLI, helper runtime, install/publish/release mechanism, framework tests, fixtures, demos, schema engine, external integration or required SDK. Reuse the developer's existing tools.

## Constraints

No automatic destructive Git operations or remote changes. No fabricated approvals/check results. Concurrent ID allocation needs conflict inspection. A fresh reviewer or independent human must verify actual work; changing role labels does not suffice.

## Decisions and Verification

[ADR-001](../decisions/ADR-001-repository-native-template.md) is an illustrative decision record. Inspect scope and file evidence and report anything not exercised; agent instructions are fallible and do not guarantee enforcement.
