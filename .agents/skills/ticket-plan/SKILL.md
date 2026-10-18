---
name: ticket-plan
description: Plan one human-led ticket iteration, assessing review findings and recording exact changes and independent checks.
---
# ticket-plan

Follow the [applicable role](../../roles/planner.md).

## Shared Rules

Repository paths in code are root-relative. Read [artifact contracts](../../../.sdd/references/artifact-contracts.md) for metadata, configuration, allowed paths, preservation, and inspection rules, and [lifecycle](../../../.sdd/references/lifecycle.md) for state/approval gates. Read the project constitution and workflow before the active artifacts; load only relevant architecture, ADRs, and source. Existing user authorization persists; request a missing decision only after preparing concrete artifacts. Never invent approvals or checks. No CLI or validator is provided.

Use before every implementation iteration, initially and after review. Inputs: ticket ID, fixed approved specification, human priorities/instructions or a request for guided questioning, existing progress and latest review. Humans drive planning through written direction or dialogue; inspect the repository and ask as many concrete questions as needed to settle material decisions. Do not require the human to restate decisions already recorded and applicable.

## Context and Preconditions

Read specification, existing plan/review/findings and actual source. Read [task/Git model](../../../.sdd/references/task-and-git-model.md) and [review policy](../../../.sdd/references/review-policy.md). Require an approved specification before finalizing a plan. After review, assess the latest run and changed repository state before proposing work. Do not rerun specification or treat a previous iteration's approval as approval of different work.

## Workflow

1. Establish actual baseline, spec revision, technical approach, affected components/interfaces/data, migration, external dependencies, alternatives and risks. Ground the approach in human engineering direction and recorded decisions. Humans own material architecture, compatibility and scope tradeoffs; present concrete options and consequences for unresolved choices before finalizing affected work. Routine implementation details may be proposed within those constraints. Do not reinterpret approved product behavior to fit a preferred implementation.
2. Assess each review finding against actual evidence, the fixed specification, project rules and human iteration context. Record validity, in/out-of-scope classification, rationale, affected tasks and proposed action in Finding Assessment. Distinguish required corrections, disputed findings, optional improvements and separate-ticket work. Do not blindly accept every suggestion or dismiss a verified requirement/security defect because it is inconvenient. Preserve finding severity and status; reviewer verification or recorded policy controls final disposition.
3. Use the [implementation template](../../../.sdd/templates/implementation.md). Write concrete Markdown describing this iteration's changes, exclusions, human direction, settled decisions and remaining questions. Split work into coherent tasks, mapped to canonical criteria or justified supporting work. Name paths, expected changes, checks, documentation impact and local changeset boundaries. Never create per-task files. For an evidence-only iteration, explicitly record that no code change is proposed and what the reviewer must recheck.
4. Check unique IDs, dependency references/cycles, stable topological order and readiness gates. Independent tasks base on an appropriate project branch; dependent tasks may form a stack. Multiple predecessor branches require an explicit base/integration decision, not an automatic merge.
5. Use the [review template](../../../.sdd/templates/review.md) to map every criterion to repeatable independent checks, boundaries, architecture/security/documentation concerns, and applicable project checks. Include finding proposals and unchanged accepted work to revalidate. Give a fresh reviewer sufficient context; do not impose tests on documentation-only work or invent commands.
6. Use plan_revision as the iteration number. Before replacing an approved iteration's narrative, retain its scope, decisions, approval evidence, task boundaries and outcomes in Iteration History. Preserve completed task IDs, changesets, evidence, findings and decisions. Reopen only tasks selected for correction, append new work, cancel obsolete unstarted work and identify affected dependent tasks. Increment plan/contract revisions for the next iteration even when requirements are unchanged; the spec stays fixed.
7. Inspect coverage, metadata, dependencies, links and boundaries. Set the new iteration's approval pending unless existing human authorization covers its actual decisions and scope. Ask targeted questions for unresolved priorities, tradeoffs or finding disputes, then obtain any missing approval of the concrete plan. Mark plan approved and ticket planned only when gates pass. Describing branches does not create them. Leave implement and review enough context to run without routine human questions.

## Outputs, Validation, and Completion

One implementation.md with the current iteration plan and preserved iteration history, plus an aligned review.md usable in a fresh session. Missing decisions/evidence/approvals leave draft or needs_reconciliation state with explicit blockers and questions. Report readiness honestly; do not implement while planning or change the fixed specification.
