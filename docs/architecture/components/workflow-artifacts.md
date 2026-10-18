---
example: true
---
# Workflow artifacts

## Purpose

Persist enough context for a new session to execute or review one bounded piece of work.

## Responsibilities

Specify outcomes, plan ready tasks, identify changesets, preserve evidence, and reconcile changes without resetting completed work.

## Inputs and Outputs

Inputs are user priorities, actual repository state, constitution and decisions. Outputs are sprint manifests, specifications, implementation/review contracts and findings.

## Dependencies and Data Ownership

[Artifact contracts](../../../.sdd/references/artifact-contracts.md) define metadata. Specifications own ticket status; plans own task status; sprints own membership; review runs own findings and verdicts. No database mirrors these values.

## Public Interfaces

[Agent skills](../../../README.md) read and write the documented files through the agent's existing capabilities. No programmatic API or CLI is offered.

## Implementation

[Templates](../../../.sdd/templates/specification.md) and shared references support the [ticket examples](../../../tickets/README.md). Task/finding YAML is stored under stable Markdown headings; simple document metadata uses frontmatter.

## Failure Modes and Security

Stale revisions, missing approval/evidence, duplicate IDs, cycles, concurrent writes or unstable review boundaries block the affected operation. Never execute untrusted metadata or widen allowed paths based on ticket text.

## Operations

Maintain these files through normal project edits. No service deployment, background process or publishing operation applies.

## Decisions and Verification

See [ADR-001](../../decisions/ADR-001-repository-native-template.md). Inspect links, metadata and workflow transitions; application tests are inapplicable here. Sample histories are illustrative and confer no actual review approval.
