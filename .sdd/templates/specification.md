---
ticket_id: "{{T-nnn}}"
title: "{{ticket title}}"
type: feature
priority: medium
story_points: null
status: draft
revision: 1
depends_on: []
external_refs: []
approval:
  state: pending
  by: null
  evidence: null
---
# {{T-nnn}}: {{ticket title}}

## Metadata

Frontmatter is authoritative for ticket-level values. Types and states follow `.sdd/references/artifact-contracts.md` and `lifecycle.md`.

Finalize requirements, scope and acceptance once with the human before planning. Keep that approved contract fixed across iterations; update only lifecycle metadata and factual history afterward. Changed product requirements need a separately authorized linked ticket.

## Summary

{{intended outcome or user story}}

## Problem / Objective

{{problem, current evidence, and measurable objective}}

## Scope

{{included behavior or technical/research outcomes}}

## Out of Scope

{{explicit exclusions}}

## Requirements

- FR-001: {{observable requirement}}
- NFR-001: {{relevant quality constraint, or explain not applicable}}

## Acceptance Criteria

- AC-001 (FR-001): {{observable outcome and verification method}}

## Dependencies

{{links/evidence for frontmatter dependencies; state none if empty}}

## Constraints

{{constitution, architecture, security, and ADR constraints}}

## Assumptions

{{explicit assumptions and validation approach}}

## Open Questions

{{unresolved questions, owner, and impact; material questions block specification completion}}

## Related Documentation

{{links to relevant project docs and decisions}}

## Change History

{{drafting history and final human approval; subsequent lifecycle transitions, iteration references and blocker/resume state without rewriting approved requirements}}
