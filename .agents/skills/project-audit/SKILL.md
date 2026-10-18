---
name: project-audit
description: Inspect SDD artifact consistency and documentation drift with evidence and scoped corrective proposals.
---
# project-audit

Follow the [applicable role](../../roles/planner.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use for an explicit audit or pre-sprint reconciliation. Inputs: scope and optional requested corrections; default to relevant current work.

## Context and Preconditions

Read scoped tickets/sprints/findings, current source/content, architecture/accepted ADRs, and actual verification evidence. Read [documentation governance](../../../.sdd/references/documentation-governance.md); load dependency/review references only when needed. Missing baseline documentation is a finding, not authorization to initialize or rewrite everything.

## Workflow

1. Record scope, actual inspected files/revisions and unavailable evidence. Check required headings/metadata, unique IDs, references, revision alignment, lifecycle approvals, cycles/readiness, membership, changesets, criterion mappings and local links.
2. Compare docs and accepted decisions with current implementation. Classify implemented, planned, partial, defect, drift and unknown observations. Structural consistency never proves semantic correctness.
3. Give findings category, severity, concrete evidence, affected paths, proposed correction, owner/ticket and confidence. Distinguish observed defects from hypotheses.
4. Put sprint reconciliation in the sprint manifest. Explicit standalone audits use the [audit template](../../../.sdd/templates/audit.md) at docs/audits/<audit-id>.md after checking existing IDs.
5. Make only authorized unambiguous mechanical corrections, recording them. Semantic/architecture changes become proposals or tickets; obtain missing material decisions before changing approved content. Never rewrite broad docs or framework files to conceal findings.
6. Recheck corrected references/diffs. Preserve existing reports and unresolved history on reruns.

## Outputs, Validation, and Completion

Evidence-backed reconciliation/audit, recorded corrections and actionable follow-up. Report checks not run and uncertainty. This is fallible agent/human inspection, with no automatic enforcement or guarantee of semantic correctness.
