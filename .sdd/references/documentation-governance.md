# Documentation governance

## Baseline and authority

`docs/README.md` indexes project knowledge. Baseline documents are `project.md`, `constitution.md`, `workflow.md`, and `architecture/{overview,platform,constraints}.md`. Use the architecture template for each architecture area with scope-specific headings. Add component, API, development, or operational documents only when there is actual content. Initialization also creates `tickets/README.md` as a navigation/convention guide, with no sprint or ticket records.

Architecture documents describe current implementation with source evidence. Label future behavior proposed, absent behavior not implemented, and inferred behavior unverified. Never turn a ticket's aspiration into a current-state claim. A documentation-only repository can state that no application runtime or deployment exists. Cite actual files; do not fabricate modules, services, dependencies, tests, or decisions.

Use component templates for substantial boundaries: purpose, responsibilities, inputs/outputs, dependencies, ownership, interfaces, failure modes, security, operations, related ADRs, and verification. Keep the constitution focused on project engineering, security, maintainability, verification policy, architecture, review, documentation, and Definition of Done.

## Decisions

ADRs live in `docs/decisions/` with stable ADR IDs and states `proposed`, `accepted`, `rejected`, or `superseded`. Record context, decision, alternatives, rationale, consequences, related components/tickets, and any predecessor. Accepted decisions cannot be silently rewritten: a new accepted ADR supersedes the old and links both directions. Capture the actual decision authority and evidence. Pending decisions remain proposed.

## Change and reconciliation

Every task declares documentation impact. Required documentation changes are part of implementation completeness, not optional cleanup. Update current-state documentation only after the behavior exists; reconcile it at ticket completion. If implementation conflicts with an accepted ADR, record a blocker and seek the appropriate decision instead of updating the ADR to conceal the conflict.

Before sprint planning inspect current source and applicable project checks, architecture and ADRs, open work, previous sprint outcomes, incomplete tasks, and unresolved review findings. Categorize observations as implemented, planned, partial, defect, drift, or unknown. Put the reconciliation report in the sprint's `Reconciliation` section using the audit finding format.

Audit findings identify category, severity, evidence, affected paths, proposed action, owner/ticket, and confidence. Structural checks cover missing artifacts/headings, invalid metadata/references, duplicate IDs, lifecycle/approval gaps, cycles, sprint membership, changesets, and broken links. Semantic checks compare current code/content with architecture, contracts, constraints, decisions, and ticket claims. Semantic inspection is fallible; state scope and uncertainty.

An audit may correct an unambiguous mechanical issue within authorized scope, recording the change. Semantic changes, architecture decisions, and unclear findings become proposals or tickets; do not rewrite documentation until it agrees with whatever happens to exist. Do not silently alter approved requirements. Use `docs/audits/<audit-id>.md` for explicitly requested standalone audits; routine sprint reconciliation belongs in the sprint, not a parallel report tree.
