---
example: true
ticket_id: "T-003"
title: "Research agent skill discovery behavior"
type: "research"
priority: "low"
story_points: 2
status: "draft"
revision: 1
depends_on: []
external_refs: []
approval:
  state: "pending"
  by: null
  evidence: null
---
# T-003: Research agent skill discovery behavior

> Illustrative example. Decisions, actors, branches, snapshots, and historical checks below are teaching records, not actual approvals, Git objects, or executed history.

## Metadata

Draft research stub, carried between illustrative sprints without changing its ID. No specification or plan approval exists.

## Summary

Compare explicit-file invocation with automatic skill discovery in selected developer environments.

## Problem / Objective

The template documents an explicit-read fallback, but automatic discovery varies. Research should produce evidence rather than assume universal compatibility.

## Scope

Not established: choose environments and a bounded manual observation protocol before specifying.

## Out of Scope

Agent adapters, SDK dependencies, scripted compatibility harnesses, CI and integration services.

## Requirements

Proposed FR-001: record evidence for selected discovery paths. This draft requirement is not an approved commitment.

## Acceptance Criteria

Proposed AC-001 (FR-001): a research note states environment/version, actual invocation, observed behavior and limitations. The environment set remains unresolved, so this criterion is not specification-ready.

## Dependencies

None. Research does not block documented explicit-file adoption.

## Constraints

Use existing tools only; no framework tests or dedicated adapters. Follow project approval/review policy.

## Assumptions

Explicitly reading the skill remains the documented fallback; automatic discovery has not been exercised across environments.

## Open Questions

Which agent environments/versions should be included? Owner: project developer. This materially affects scope and blocks specified status.

## Related Documentation

[Platform limitations](../../docs/architecture/platform.md); [adoption guide](../../docs/development/adoption.md).

## Change History

Illustrative sprint-001 deferred this stub for capacity and carried it to sprint-002. Same ticket ID, status draft, no tasks or review artifacts generated. No completed work was reset.
