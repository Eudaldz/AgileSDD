---
name: ticket-review
description: Independently review actual SDD changes and append evidence-backed findings and verdicts.
---
# ticket-review

Follow the [applicable role](../../roles/reviewer.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use for review/re-review of a ticket or named task. Inputs: ticket ID, optional task ID, identifiable changeset boundary.

## Context and Preconditions

Read specification, implementation/review contracts, existing findings and actual diffs/files. Read [review policy](../../../.sdd/references/review-policy.md) and [task/Git model](../../../.sdd/references/task-and-git-model.md). Require aligned revisions and a stable scope. If you implemented the work, prepare handoff and report independence unavailable; do not self-approve or delegate without authorization.

## Workflow

1. Verify actual base/commits/snapshot and paths, including untracked files. Missing evidence, unstable scope or stale revisions block approval; inspect available evidence without claiming completeness.
2. Independently check each criterion, behavior/regressions, dependencies, architecture/ADRs, security, project checks and documentation. Run inspected applicable checks and state limitations.
3. Append a run using the [findings template](../../../.sdd/templates/review-findings.md), with reviewer, exact revisions/boundary, scope, checks/outcomes, limitations and verdict. Reuse finding IDs for the same defect and append history.
4. Record evidence, paths/lines where known, severity, category, task and suggested fix. Requested fixes yield changes_requested; unavailable evidence yields blocked. Verify fixes before resolving findings. Never delete old findings or verdicts.
5. Accept tasks only when their gates pass. Full-ticket acceptance additionally requires all required tasks accepted, criteria verified, dependencies satisfied, docs current and blockers resolved or dispositioned by an authorized human under policy.
6. Record accepted only with evidence/authority; done additionally requires the completion gate and reviewer/human action. Do not edit implementation during normal review, merge, push or publish.

## Outputs, Validation, and Completion

Append-only findings/runs and eligible state changes. Report actual independence and unavailable checks. Re-review identifies the new boundary and preserves resolution attempts. Missing context leaves an explicit blocked verdict, never assumed acceptance.
