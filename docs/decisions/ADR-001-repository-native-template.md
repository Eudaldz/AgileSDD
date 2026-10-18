---
example: true
adr_id: ADR-001
title: Deliver a repository-native template
status: accepted
supersedes: null
---
# ADR-001: Deliver a repository-native template

This accepted record is illustrative, including its decision authority; it is not a claim of a real historical approval.

## Context

The sample project's deliverable is a public example developers can copy or study. A dedicated runtime would introduce installation and maintenance work unrelated to that purpose.

## Decision

Keep skills, references, templates and project artifacts as ordinary repository text. Use existing editing and Git capabilities. Deliver no CLI, package, publishing workflow or framework test suite.

## Alternatives

A Python CLI could enforce structural rules but would require a runtime and software maintenance. A hosted orchestration service would add accounts and external state. Both exceed the template's scope.

## Rationale

Transparent files let developers adapt the workflow to their language, agent and project practices. Explicit contracts provide useful checks without claiming automated enforcement.

## Consequences

Adoption requires no package installation. Checks are performed by agents/humans and can miss errors. IDs are not allocated atomically and independent review still needs a real separate reviewer.

## Related Components and Tickets

[Workflow artifacts](../architecture/components/workflow-artifacts.md); [T-001](../../tickets/T-001/specification.md).

## Decision Record

Illustrative project owner decision D-001 in T-001's sample history. No actual human approval is inferred from this teaching record.
