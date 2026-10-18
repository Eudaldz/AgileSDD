---
example: true
---
# Architecture overview

## Status and Evidence

Current file-based architecture. Evidence: [.agents skills](../../.agents/skills/sdd-init/SKILL.md), [artifact contracts](../../.sdd/references/artifact-contracts.md), [defaults](../../.sdd/defaults.yaml), and [ticket examples](../../tickets/README.md). No executable service is present.

## Responsibilities and Boundaries

`.agents/` defines reusable behavior; `.sdd/` defines reusable templates and conventions. `docs/` owns current project knowledge; `tickets/` owns planning and review history. Normal project work leaves reusable behavior unchanged.

## Structure and Data Flow

Human goal -> sprint reconciliation/proposal -> specification -> implementation and independent review contracts -> task evidence -> findings -> fixes/re-review -> accepted work and synchronized docs. Git preserves changes; no database or service orchestrates the flow.

## Platform and Dependencies

A coding agent or human reads/edits Markdown and YAML. Git is useful for identified review changesets, with an explicit working-tree fallback. There is no mandatory programming language, package manager, model, IDE, agent SDK or external service.

## Constraints

Preserve stable IDs and completed work. Check approval/state gates and report uncertainty; instructions do not enforce a sandbox. Never claim a sample branch or review identity is real evidence.

## Decisions and Verification

[ADR-001](../decisions/ADR-001-repository-native-template.md) illustrates the template-only decision. [Workflow artifacts](components/workflow-artifacts.md) describes the main component. Structural inspection can establish internal consistency; it cannot establish semantic correctness across arbitrary adopting projects.
