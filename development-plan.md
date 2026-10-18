# Development Plan: Agile Spec-Driven Development Public Template

## 0. Mission and instructions for the coding agent

Build a small, reusable, repository-native Spec-Driven Development (SDD) template that demonstrates sprint planning, ticket specification, implementation planning, implementation, independent review, documentation governance, and reconciliation through coding-agent skills and Markdown artifacts.

The result must be a public template repository that developers can copy, use directly, or study as an example. Deliver files locally; creating or publishing the public repository is outside this task.

Include only files that belong in a developer project using this workflow: reusable skills and references, document templates, project documentation, and representative sprint/ticket artifacts. Do not add a CLI, helper-script runtime, template package manifests, installers, publishing or release mechanisms, framework tests, fixtures, or separate demo applications.

Application tests in an adopting project remain governed by that project's engineering practices. References to tests below describe that project work; they do not require a test suite in this template repository.

The framework must be:

- **Agent-native:** workflows are exposed primarily as reusable coding-agent skills.
- **Agent-portable:** core behavior must not depend on a proprietary model, IDE, or coding-agent SDK.
- **Project-agnostic:** skills, templates, and artifact conventions work for any technology stack.
- **Agile-native:** sprints are short planning cycles; specifications and tickets can evolve across sprints.
- **Repository-native:** Git and Markdown are the fundamental persistence mechanisms.
- **Human-reviewable:** all important decisions, specifications, plans, and review findings are readable Markdown.
- **Incremental:** rerunning skills updates existing artifacts without destroying completed work.
- **Explicit and inspectable:** document precise rules for identifiers, artifact checks, state transitions, and dependencies. Do not claim programmatic enforcement where none exists.
- **Documentation-driven:** project architecture and documentation remain synchronized with implementation.
- **Independent-review capable:** implementation and review are separate roles with different instructions and outputs.

Implement this system incrementally, according to the milestones in this specification.

Do not build a CLI, helper scripts, external integrations, web UI, services, remote orchestration, packaging, publishing, release automation, or framework test suite.

Make reasonable implementation decisions when unspecified. Document important assumptions and avoid introducing unnecessary complexity.

---

# 1. Fundamental architectural principles

## 1.1 Separate framework from project state

The repository has four top-level SDD directories.

### `.agents/` — Reusable agent behavior

Contains skills and role definitions describing how coding agents execute workflows.

Must contain no project-specific knowledge.

### `.sdd/` - Reusable templates and conventions

Contains document templates, shared references, metadata contracts, and configuration defaults. No executable tooling or runtime dependencies are required.

Must remain project-independent.

### `docs/` — Project-specific knowledge

Contains everything necessary for a human or coding agent to understand the current state of the project.

Includes:

- Project constitution.
- Project goals and product context.
- Architecture.
- Technical constraints.
- Architecture Decision Records.
- Component descriptions.
- API contracts and interfaces.
- Engineering guidelines.
- Operational documentation.
- Project-specific SDD settings.

### `tickets/` — Project-specific development state

Contains:

- Sprint manifests.
- Ticket specifications.
- Implementation plans and tasks.
- Review instructions.
- Review findings.
- Ticket lifecycle information.
- Traceability to code changes and documentation updates.

## 1.2 Framework immutability

During normal project development:

- Skills must not modify `.agents/`.
- Skills must not modify `.sdd/`.
- Project-specific configuration must live inside `docs/`.
- No ticket may redefine framework-level instructions.
- Normal SDD skills may modify only explicitly permitted project paths.

Framework development itself is an exception: contributors working on the framework repository may intentionally modify `.agents/` and `.sdd/`.

Document allowed write paths and require skills to check intended edits and inspect the resulting diff. This workflow boundary is not a programmatic sandbox or guarantee of enforcement.

## 1.3 Source-of-truth rules

| Concern | Authority |
|---|---|
| Agent workflow behavior | `.agents/` |
| Artifact structure and validation | `.sdd/` |
| Project-wide development principles | `docs/constitution.md` |
| Current architecture | `docs/architecture/` |
| Accepted technical decisions | `docs/decisions/` |
| Project-specific workflow configuration | `docs/workflow.md` |
| Intended ticket behavior | `tickets/<id>/specification.md` |
| Technical implementation strategy | `tickets/<id>/implementation.md` |
| Independent verification requirements | `tickets/<id>/review.md` |
| Actual review results | `tickets/<id>/review-findings.md` |
| Actual implemented behavior | Source code and project verification evidence, including application tests when applicable |
| Sprint membership and planning commitments | Sprint manifests |

If two sources disagree, do not silently choose whichever is most convenient. Report the conflict and resolve it using the appropriate workflow.

---

# 2. Repository structure

Use the following structure as a guide. Optional documentation areas should exist only when the sample project needs them:

```text
repository/
│
├── .agents/
│   ├── skills/
│   │   ├── sdd-init/
│   │   │   └── SKILL.md
│   │   ├── sdd-sprint/
│   │   │   └── SKILL.md
│   │   ├── ticket-spec/
│   │   │   └── SKILL.md
│   │   ├── ticket-plan/
│   │   │   └── SKILL.md
│   │   ├── ticket-implement/
│   │   │   └── SKILL.md
│   │   ├── ticket-review/
│   │   │   └── SKILL.md
│   │   ├── ticket-reconcile/
│   │   │   └── SKILL.md
│   │   └── sdd-audit/
│   │       └── SKILL.md
│   │
│   └── roles/
│       ├── planner.md
│       ├── implementer.md
│       └── reviewer.md
│
├── .sdd/
│   ├── templates/
│   │   ├── constitution.md
│   │   ├── project.md
│   │   ├── workflow.md
│   │   ├── architecture.md
│   │   ├── component.md
│   │   ├── adr.md
│   │   ├── sprint.md
│   │   ├── specification.md
│   │   ├── implementation.md
│   │   ├── review.md
│   │   ├── review-findings.md
│   │   └── audit.md
│   │
│   ├── references/
│   │   ├── lifecycle.md
│   │   ├── artifact-contracts.md
│   │   ├── task-and-git-model.md
│   │   ├── documentation-governance.md
│   │   └── review-policy.md
│   │
│   └── defaults.yaml
│
├── docs/
│   ├── README.md
│   ├── constitution.md
│   ├── project.md
│   ├── workflow.md
│   ├── architecture/
│   │   ├── overview.md
│   │   ├── platform.md
│   │   ├── constraints.md
│   │   └── components/
│   ├── decisions/
│   ├── api/
│   ├── development/
│   └── operations/
│
├── tickets/
│   ├── README.md
│   ├── sprints/
│   │   ├── sprint-001.md
│   │   └── ...
│   │
│   ├── T-001/
│   │   ├── specification.md
│   │   ├── implementation.md
│   │   ├── review.md
│   │   └── review-findings.md
│   │
│   └── ...
│
├── README.md
└── .gitignore
```

This repository itself is the example developer project. Keep its example context in `docs/` and illustrative work in `tickets/`; label sample content and explain how to replace it. Do not create separate examples, tests, fixtures, or demo applications. Create documentation directories only when useful content exists. This development plan is an authoring input, not a required adoption artifact; do not add internal build-progress documents.

Workflow artifacts must have clear templates and documented metadata contracts, using simple YAML frontmatter or structured Markdown without a schema-validation runtime.

---

# 3. Technology and implementation choices

## 3.1 Template format

Use Markdown for skills, references, and human-facing artifacts; YAML frontmatter for structured metadata; and a small YAML defaults file for reusable options.

Agents use their existing file-editing capabilities and local Git tools. Do not impose a programming language, package manager, dependency, build step, installation step, or dedicated runtime. Describe structural checks as reviewable instructions rather than building a validation engine.

---

## 3.2 Skills

Implement skills according to the Agent Skills convention:

```text
skill-name/
└── SKILL.md
```

Each `SKILL.md` must contain valid YAML frontmatter with at least:

```yaml
---
name: ticket-plan
description: Create or revise the implementation plan and verification instructions for an SDD ticket.
---
```

Each skill should describe:

1. Purpose.
2. Activation conditions.
3. Required inputs.
4. Context-loading procedure.
5. Preconditions.
6. Workflow steps.
7. Expected outputs.
8. Validation requirements.
9. Error handling.
10. Completion criteria.

Keep skills concise. Put shared implementation details in `.sdd/references/` rather than copying them into every skill.

## 3.3 Agent compatibility

Do not assume slash commands are universally supported.

The canonical interface is the skill name and its instructions. When an agent supports slash commands, skills may be invoked using the corresponding `/skill-name` convention.

Skills operate directly on repository files using the agent's existing capabilities. Slash-style invocations below are agent skill notation, not a shell CLI to implement.

Developers use the repository template or manually copy `.agents/` and `.sdd/` into existing projects, then invoke `sdd-init` through their agent. Explain how to replace sample state without overwriting existing work. No bootstrap or installation command is required.

Do not build dedicated integrations for every agent in v1.

---

# 4. Project initialization

## Skill invocation

`/sdd-init`

## Purpose

Initialize SDD in a new or existing repository.

## Inputs

- Repository location.
- Optional project description.
- Optional architectural preferences.
- Optional engineering principles.
- Optional project-specific workflow configuration.

## Workflow

### Step 1 — Inspect repository

Determine whether the project is:

- Empty or nearly empty.
- An existing software repository.
- Already initialized with SDD.

Inspect:

- Directory structure.
- Source code.
- Build system.
- Dependency manifests.
- Existing README and documentation.
- Testing infrastructure.
- CI/CD configuration.
- Infrastructure configuration.
- Git state.

Ignore generated files, dependencies, build artifacts, and irrelevant vendor directories.

### Step 2 — Bootstrap project knowledge

For a new repository:

- Ask for product purpose.
- Ask for known technology or architecture constraints.
- Ask for major engineering conventions.
- Generate initial project documentation.

For an existing repository:

- Infer the current architecture from evidence.
- Identify major modules and components.
- Inspect actual dependencies.
- Document entry points and service boundaries.
- Identify test infrastructure.
- Identify existing architectural decisions.
- Mark uncertain findings as unverified.

Do not invent architecture details.

### Step 3 — Create project directories

Create and populate:

```text
docs/
tickets/
```

Do not create actual sprint files or tickets yet.

Use framework templates from `.sdd/templates/`.

### Step 4 — Establish constitution

Create `docs/constitution.md`.

Include:

- Engineering principles.
- Maintainability expectations.
- Security principles.
- Testing expectations.
- Documentation requirements.
- Architecture compliance rules.
- Code-review requirements.
- Definition of Done.

This is project-specific, even though its template is reusable.

### Step 5 — Establish documentation baseline

Generate initial project documentation from the actual repository.

Architecture that has not been implemented must be marked as proposed.

### Step 6 — Validate initialization

Verify:

- Project docs exist.
- Required headings are present.
- Project configuration is valid.
- No project-specific information was written into `.agents/` or `.sdd/`.
- No source code was modified unnecessarily.

## Idempotency

Rerunning `/sdd-init` must not overwrite approved project documentation.

It should identify missing documents and propose updates to stale documentation.

---

# 5. Sprint planning

## Skill invocation

`/sdd-sprint`

## Purpose

Prepare one bounded sprint of work from the current state of the repository, previous work, and user instructions.

This skill must never attempt to plan the full product roadmap unless explicitly requested.

## Inputs

- Sprint goal.
- User instructions.
- Optional sprint dates.
- Optional sprint capacity.
- Optional desired story-point scale.
- Optional carryover tickets.
- Optional external ticket references.

## Pre-planning reconciliation

Before planning any sprint:

1. Inspect current source code and tests.
2. Read project documentation.
3. Read constitution and accepted ADRs.
4. Inspect existing open tickets.
5. Inspect the previous sprint.
6. Identify incomplete tasks.
7. Inspect unresolved review findings.
8. Check documentation inconsistencies.
9. Identify architectural risks or missing information.
10. Produce a reconciliation report.

The agent must distinguish:

- Implemented functionality.
- Planned but unimplemented functionality.
- Partially implemented functionality.
- Unresolved defects.
- Documentation drift.
- Unknown or unverified areas.

## Sprint planning behavior

The agent proposes a sprint based on:

- User priorities.
- Existing project state.
- Open work.
- Dependency ordering.
- Estimated effort.
- Capacity, when supplied.
- Technical and architectural prerequisites.

Ask targeted questions when uncertainty materially changes scope, priority, or technical feasibility.

Ticket types must include:

- Feature.
- Bug.
- Refactor.
- Architecture.
- Design.
- Documentation.
- Research/spike.
- Infrastructure.
- Technical debt.

Architecture and research tickets are legitimate deliverables, even if they do not produce application code.

## Sprint output

Create:

```text
tickets/sprints/sprint-001.md
```

Include:

- Sprint ID.
- Sprint goal.
- Dates, if supplied.
- Capacity, if supplied.
- Proposed tickets.
- Story points.
- Priority.
- Dependencies.
- Carryover items.
- Major risks.
- Sprint acceptance conditions.
- Reconciliation findings.

Create a ticket directory for every approved ticket.

Initially create only:

```text
tickets/T-001/specification.md
```

This is a ticket stub, not necessarily a completed specification.

Do not generate implementation plans for every ticket during sprint planning.

## Story points

Story points apply to the whole ticket, not individual implementation tasks.

They express relative effort, complexity, and uncertainty.

The framework must support project-configured scales, with Fibonacci-like values as a reasonable default.

Do not claim that LLM-generated estimates are objectively reliable.

## Ticket identity

Ticket IDs must be unique across the repository and independent of sprint IDs.

A ticket may be moved between sprints while retaining its ID and history.

External IDs such as Jira keys are optional metadata.

## Human approval

The agent should propose the sprint and allow a human to revise it before finalizing ticket creation.

---

# 6. Ticket lifecycle

Define the following lifecycle states:

```text
draft
  ↓
specified
  ↓
planned
  ↓
in_progress
  ↓
in_review
  ↓
accepted
  ↓
done
```

Additional states:

```text
blocked
cancelled
```

Revisions may move tickets backward when necessary.

Examples:

- Planned → Specified when product requirements change.
- In Review → In Progress when findings need fixes.
- Done → Specified when a previously completed ticket is explicitly reopened.

Do not automatically reopen completed work because a new sprint introduces an enhancement. Prefer a new linked ticket for independently deliverable changes.

## Lifecycle rules

- A ticket cannot become planned without a valid specification.
- Implementation requires a reviewed implementation plan.
- A ticket cannot become accepted with unresolved blocking review findings.
- A ticket cannot become done when required documentation changes are incomplete.
- A cancelled ticket retains its history.
- Skills must check documented transition preconditions and record evidence before changing state; no automated enforcement is provided.

Each ticket artifact should include a stable ticket ID in its metadata.

The specification is authoritative for ticket-level metadata such as title, type, priority, story points, status, and external references. Other artifacts reference the ID rather than maintaining independent copies.

---

# 7. Ticket specification

## Skill invocation

`/ticket-spec <ticket-id>`

## Output

```text
tickets/<ticket-id>/specification.md
```

## Responsibilities

Read:

- Existing ticket stub or specification.
- User's new instructions.
- Project constitution.
- Relevant architecture documents.
- Existing ADRs.
- Relevant application code.
- Dependencies on other tickets.

Produce:

- Problem statement.
- Objective.
- Scope.
- Out-of-scope items.
- User stories or technical outcomes.
- Functional requirements.
- Non-functional requirements.
- Constraints.
- Acceptance criteria.
- Dependencies.
- Assumptions.
- Open questions.

Every functional requirement must have a stable ID:

```text
FR-001
FR-002
FR-003
```

Every acceptance criterion must have a stable ID:

```text
AC-001
AC-002
AC-003
```

Technical tickets may define design or research outcomes instead of end-user behavior.

## Revision handling

When changing an existing specification:

1. Read the previous specification.
2. Compare it with the requested change.
3. Preserve unchanged requirement IDs.
4. Add new requirement IDs.
5. Explicitly mark removed or superseded requirements.
6. Identify the impact on the implementation plan.
7. Identify already implemented behavior that may need revision.
8. Preserve relevant human decisions.

Do not silently rewrite the entire specification.

When changes are material, mark downstream plans and reviews as needing reconciliation.

---

# 8. Implementation planning

## Skill invocation

`/ticket-plan <ticket-id>`

## Outputs

```text
tickets/<ticket-id>/implementation.md
tickets/<ticket-id>/review.md
```

## Purpose

Transform an approved specification into two optimized execution contracts:

- Implementation instructions for the implementer agent.
- Verification instructions for the reviewer agent.

The plan must be a single Markdown document containing technical design, tasks, ordering, and acceptance criteria.

Do not create separate task files.

## Implementation plan structure

`implementation.md` must contain:

### Metadata

- Ticket ID.
- Specification revision reference.
- Plan revision.
- Status.
- Last planning date.
- Human approval state.

### Context

- Ticket goal.
- Relevant architecture.
- Existing implementation state.
- Constraints.
- Applicable ADRs.

### Technical approach

- Proposed architecture.
- Affected components.
- Data structures.
- Interfaces.
- External dependencies.
- Migration considerations.
- Risk analysis.
- Alternatives when material.

### Acceptance criteria

Reference criteria defined in `specification.md`.

Preserve the canonical IDs and wording.

### Ordered implementation tasks

Tasks must include:

- Stable task ID.
- Description.
- Dependencies.
- Expected files or components.
- Expected changes.
- Required project verification, including application tests when applicable.
- Documentation impact.
- Acceptance criteria covered.
- Estimated scope or complexity when useful.
- Status.
- Changeset information.

### Validation plan

Choose checks appropriate to the adopting project and change. Application work may include the following; template and documentation work uses artifact inspection and a walkthrough without adding a test harness:

- Unit tests.
- Integration tests.
- Contract tests where applicable.
- Static analysis.
- Formatting checks.
- Manual verification where necessary.

### Documentation plan

Identify affected documentation.

### Risks and unresolved decisions

Do not hide technical uncertainty.

## Revision behavior

When `/ticket-plan` is rerun:

- Compare the latest specification against the existing plan.
- Preserve completed tasks and their traceability.
- Update unstarted tasks when needed.
- Append new tasks for additional work.
- Mark obsolete tasks as cancelled or superseded.
- Flag completed tasks invalidated by changed requirements.
- Recalculate dependency order.
- Regenerate affected review instructions.

Never reset task completion checkboxes merely because the plan was regenerated.

Allocate stable IDs by inspecting existing records; preserve revision references and resolve conflicts before writing. Never renumber completed tasks.

---

# 9. Task and changeset model

A ticket may contain multiple implementation tasks.

Each task should represent one coherent and independently reviewable change.

## Task metadata example

```yaml
id: TASK-001
title: Define authentication interfaces
status: pending
depends_on: []
acceptance_criteria:
  - AC-001
changeset:
  branch: null
  base_branch: null
  commit: null
  external_pr: null
```

Represent this metadata within the implementation Markdown using a documented machine-readable convention.

The canonical task list remains human-readable.

## Task states

```text
pending
ready
in_progress
implemented
in_review
accepted
blocked
cancelled
```

## Dependencies

Document dependency checks in shared references and require skills to follow them before selecting tasks. Missing references and cycles block progress; no validation tool is required.

Requirements:

- Task IDs must be unique.
- Dependencies must reference existing tasks.
- Circular dependencies are forbidden.
- A task is ready only when required predecessor tasks have reached the configured acceptable state.
- A stable topological ordering must be available.
- Unrelated tasks may run independently.

## One task, one changeset

The intended relationship is:

```text
Ticket
  ├── Task 1 → Changeset 1 → PR 1
  ├── Task 2 → Changeset 2 → PR 2
  └── Task 3 → Changeset 3 → PR 3
```

A changeset is the framework's provider-independent review unit.

It should capture:

- Branch name.
- Base branch.
- Associated commits.
- Changed-file list.
- Validation evidence.
- Review state.
- Optional external PR URL or ID.

One task should map to one logical changeset. That does not necessarily mean one commit.

## Stacked PR support

For dependent tasks, support a stack:

```text
main
  └── ticket/T-001/task-001
       └── ticket/T-001/task-002
            └── ticket/T-001/task-003
```

Required behavior:

- Determine an appropriate base branch from task dependencies.
- Never invent a dependency when tasks are independent.
- Detect working-tree changes before branch operations.
- Never discard uncommitted work.
- Never force-push without explicit authorization.
- Preserve task-to-branch traceability.
- Support local Git operation without a GitHub account.
- Record external PR references only when available.

A task may produce a documentation-only changeset.

For tasks that are purely exploratory and do not produce a meaningful changeset, document the exception rather than creating an empty PR.

Do not automate remote PR creation in v1.

---

# 10. Implementation agent

## Skill invocation

`/ticket-implement <ticket-id>`

Optionally support a specific task:

`/ticket-implement <ticket-id> <task-id>`

## Role

The implementer executes approved technical plans.

## Required context

Read:

1. Project constitution.
2. Ticket specification.
3. Ticket implementation plan.
4. Relevant architecture documentation.
5. Applicable ADRs.
6. Relevant existing source code.
7. Existing task state.

Do not load the entire repository indiscriminately.

## Execution procedure

1. Validate the ticket and plan.
2. Determine ready tasks.
3. Select one task or the next dependency-ready task.
4. Establish the associated changeset boundary.
5. Implement the task.
6. Add or update application tests when required by the project and change; template-only work does not require tests.
7. Execute applicable validation commands.
8. Update affected documentation.
9. Record implementation evidence.
10. Update task status.
11. Prepare the next task only when dependencies permit.

## Implementation constraints

- Do not silently change ticket requirements.
- Do not edit `.agents/` or `.sdd/`.
- Respect accepted ADRs.
- Do not overwrite unrelated work.
- Do not invent completed test results.
- Do not mark tasks accepted on behalf of the reviewer.
- Do not mark tickets done automatically.
- Do not bypass validation failures.

The implementer may record technical concerns and propose a revised plan.

It must not silently alter acceptance criteria to fit the implemented code.

## Documentation requirements

Every task must declare its documentation impact:

```text
none
update-existing
create-new
architecture-decision-required
```

When documentation changes are required, they must be included in the task's changeset.

A task should not be considered implementation-complete when required documentation is missing.

---

# 11. Independent reviewer agent

## Skill invocation

`/ticket-review <ticket-id>`

Optionally:

`/ticket-review <ticket-id> <task-id>`

## Purpose

Perform a code-review-like verification without depending on GitHub or another hosting provider.

## Required inputs

- `specification.md`
- `implementation.md`
- `review.md`
- Actual code changes.
- Relevant architecture documents.
- Accepted ADRs.
- Applicable project verification results.
- Existing review findings.

The reviewer should inspect actual code and diffs rather than trusting implementer summaries.

## Review contract

`review.md` must contain:

- Scope of review.
- Specification revision being reviewed.
- Task/changeset boundaries.
- Applicable acceptance criteria.
- Functional verification checklist.
- Architecture compliance checklist.
- Security considerations.
- Testing requirements.
- Documentation verification.
- Performance considerations where relevant.
- Required reporting format.

The initial review contract is produced during planning.

The implementer should not modify it to weaken requirements.

When specifications materially change, rerun planning and review-contract generation.

## Reviewer behavior

1. Verify the correct changeset is being reviewed.
2. Inspect relevant diffs.
3. Check behavior against acceptance criteria.
4. Check architecture compliance.
5. Inspect tests and validation evidence.
6. Run appropriate independent checks when available.
7. Check documentation accuracy.
8. Identify bugs, regressions, missing functionality and maintainability concerns.
9. Record actionable findings.
10. Provide an overall review verdict.

## Review findings

Write results to:

```text
tickets/<ticket-id>/review-findings.md
```

Each finding must have:

- Stable ID.
- Ticket and task ID.
- Severity.
- Category.
- Description.
- Evidence.
- File and line reference when available.
- Suggested resolution.
- Status.
- Reviewer run identifier.
- Resolution notes.

Severity levels:

```text
critical
major
minor
suggestion
```

Finding states:

```text
open
acknowledged
resolved
wont_fix
```

`wont_fix` must require an explicit recorded decision and rationale.

## Review verdicts

Support:

```text
approved
changes_requested
blocked
```

The reviewer can approve a task only when blocking findings are resolved or explicitly dispositioned under project policy.

Reviewing the full ticket must additionally verify:

- All required tasks are accepted.
- All acceptance criteria are satisfied.
- Documentation is synchronized.
- Required project checks pass, including application tests when applicable.
- Task dependencies are satisfied.

## Local review independence

The reviewer must work with local Git diffs, commits, and branches.

An external PR is optional.

The review instructions must be usable in a separate coding-agent session.

Prefer an independent reviewer agent without relying on the implementer's previous conversation context.

---

# 12. Review reconciliation

## Skill invocation

`/ticket-reconcile <ticket-id>`

## Purpose

Reconcile review findings with implementation state.

## Procedure

1. Read all open findings.
2. Match findings to tasks and files.
3. Determine whether each finding requires:
   - A fix to an existing task.
   - A new implementation task.
   - A plan revision.
   - A specification revision.
   - A documentation update.
4. Preserve the original finding history.
5. Apply only justified status changes.
6. Rerun validation when necessary.
7. Identify tasks that require re-review.

Review findings must never be deleted merely because the implementer claims a fix.

A finding becomes resolved only when there is sufficient evidence.

The reviewer ultimately determines acceptance, unless a human explicitly overrides the finding under recorded project policy.

---

# 13. Documentation governance

The `docs/` directory is the project's persistent knowledge base.

It must be readable by both humans and coding agents.

## Mandatory baseline documents

### `docs/README.md`

Documentation index and navigation.

### `docs/project.md`

- Product purpose.
- Current project scope.
- Stakeholders or user roles, if relevant.
- Major capabilities.
- Project boundaries.

### `docs/constitution.md`

- Engineering principles.
- Security.
- Testability.
- Code quality.
- Architecture rules.
- Documentation obligations.
- Review policy.

### `docs/workflow.md`

Project-specific options for the reusable SDD framework.

### `docs/architecture/overview.md`

High-level system architecture.

### `docs/architecture/platform.md`

Runtime architecture, deployment, infrastructure, dependencies, and platform services.

### `docs/architecture/constraints.md`

Accepted technical constraints and boundaries.

## Component documentation

For each important component, create standardized documentation containing:

- Purpose.
- Responsibilities.
- Inputs and outputs.
- Dependencies.
- Data ownership.
- Public interfaces.
- Important implementation details.
- Failure modes.
- Security considerations.
- Operational considerations.
- Related ADRs.
- Relevant tests.

Only create component documents when relevant.

## Architecture Decision Records

Use standard ADRs inside:

```text
docs/decisions/
```

Each ADR must include:

- ID.
- Title.
- Status.
- Context.
- Decision.
- Alternatives.
- Rationale.
- Consequences.
- Related components.
- Related tickets.
- Superseded ADR reference, if applicable.

Support:

```text
proposed
accepted
rejected
superseded
```

Accepted ADRs must not be silently edited to change their original decision.

When a decision is replaced, create a new ADR that supersedes the previous one.

## Current-state documentation rule

`docs/architecture/` describes the current implementation.

A planned architecture change must not be presented as already implemented.

The ticket and proposed ADR may describe the future design.

Once implementation is accepted, current-state documentation must be reconciled.

---

# 14. Project-specific workflow settings

Implement a reusable configuration template that generates:

```text
docs/workflow.md
```

Use YAML frontmatter for machine-readable options.

Example:

```yaml
---
sdd:
  story_points: [1, 2, 3, 5, 8, 13]
  default_sprint_length_days: 14
  require_spec_approval: true
  require_plan_approval: true
  require_independent_review: true
  require_docs_validation: true
  git:
    mode: local
    stacked_changesets: true
  validation:
    fail_on_broken_links: true
    require_acceptance_traceability: true
---
```

These values are examples and must be validated.

Project-specific testing commands and supported validation tools can also be configured here.

The framework must supply defaults when fields are absent.

Invalid settings should generate clear errors, not silently change workflow behavior.

---

# 15. Continuous reconciliation and drift prevention

## Skill invocation

`/sdd-audit`

## Purpose

Inspect the repository and identify inconsistencies between project state, implementation, specifications, documentation, and review artifacts.

The command should be callable independently and must run as part of sprint planning.

## Levels

### Structural validation

The agent inspects the following using documented contracts and existing repository tools; no bundled validator is provided.

Deterministic checks:

- Required files.
- Valid frontmatter.
- Valid IDs.
- Duplicate IDs.
- Broken references.
- Invalid state transitions.
- Task dependency cycles.
- Missing acceptance mappings.
- Missing documentation references.
- Invalid sprint memberships.
- Missing changeset metadata.

### Semantic reconciliation

Agent-assisted checks:

- Documentation inconsistent with code.
- Architecture description inconsistent with implementation.
- Constraints violated.
- Accepted decisions not reflected in code.
- Tickets describing behavior that no longer matches the implementation.
- Incomplete or misleading implementation status.
- Unresolved findings affecting current work.

### Documentation reconciliation

Check:

- Component documentation.
- API descriptions.
- Architecture diagrams when present.
- Deployment assumptions.
- Configuration documentation.
- Engineering instructions.

Prefer checking against source artifacts and executable evidence where possible.

## Output

Generate a sprint audit or explicit standalone audit artifact.

Every finding must include:

- Category.
- Severity.
- Evidence.
- Affected files.
- Proposed corrective action.
- Suggested owner or ticket.
- Confidence or uncertainty where appropriate.

## Correction rules

Automatically fix safe mechanical inconsistencies only.

For semantic changes, architecture changes, and uncertain conclusions:

- Propose a correction.
- Request human approval when needed.
- Create or update tickets when appropriate.

Do not automatically rewrite large portions of documentation to make audits pass.

Do not assume that an LLM review guarantees semantic correctness.

---

# 16. Sprint and ticket persistence rules

## Sprint files

Sprint manifests should reference ticket IDs.

They must not duplicate entire ticket specifications.

Example:

```markdown
# Sprint 003

## Goal
Improve search quality and reliability.

## Tickets

| ID | Title | Points | Status |
|---|---|---:|---|
| T-014 | Add document filters | 3 | planned |
| T-015 | Improve ranking | 5 | draft |
```

Machine-readable sprint membership and metadata should be represented consistently, preferably with YAML frontmatter or a single structured section.

Avoid maintaining two independently editable sources for the same value.

## Ticket files

One directory per ticket.

Store the four ticket artifacts:

```text
specification.md
implementation.md
review.md
review-findings.md
```

Only `specification.md` is required during initial sprint planning.

Create the others as the ticket progresses.

## Sprint changes

Support:

- Moving tickets between sprints.
- Deferring tickets.
- Carrying unfinished work into the next sprint.
- Adding urgent tickets mid-sprint.
- Changing estimates with recorded rationale.
- Splitting oversized tickets into linked successor tickets.
- Cancelling tickets without losing history.

Completed tickets should remain readable and traceable.

---

# 17. Direct repository workflows and adoption

Skills describe initialization, artifact inspection, sprint and ticket creation, state updates, task selection, review, and auditing. Agents perform these operations directly with existing file and Git tools.

Shared references must define:

- Unique ID allocation by inspecting existing records.
- Required metadata, headings, references, and lifecycle preconditions.
- Dependency checks and stable ordering of ready tasks.
- Allowed write paths and preservation of approved content and unrelated changes.
- Conflict detection and reporting of incomplete checks.
- Local Git state inspection before branch or changeset operations.

Validation means following documented checks and recording evidence. Do not claim automatic enforcement.

The README explains using the public repository as a template, copying reusable directories into existing projects, invoking skills, and replacing sample state. Include no CLI, installer, package distribution, publishing commands, or release workflow.

---

# 18. Agent roles and context management

Define three roles.

## Planner

Responsible for:

- Sprint planning.
- Ticket specification.
- Technical planning.
- Dependency decomposition.
- Review-contract generation.

Must not implement unrelated code while planning.

## Implementer

Responsible for:

- Executing approved tasks.
- Writing code.
- Updating application tests when required by the adopting project and change.
- Updating current-state documentation.
- Recording implementation evidence.

Must not self-approve implementation.

## Reviewer

Responsible for:

- Independent verification.
- Finding defects.
- Checking requirements.
- Checking architecture compliance.
- Checking documentation.
- Reporting actionable findings.
- Recording review verdicts.

Must not rewrite implementation code as part of a normal review.

## Context optimization

Each skill should load only relevant documentation and artifacts.

Implement a consistent context-loading procedure:

1. Read project constitution.
2. Read the active ticket.
3. Read role-specific artifact.
4. Read relevant architecture docs and ADRs.
5. Inspect relevant source code.
6. Expand context only when needed.

The entire repository must not be loaded by default.

The implementation and review artifacts should be written so a fresh agent session can execute them without needing the original planning conversation.

---

# 19. Required template contracts

Implement standardized templates for all generated documents.

## Specification template

Required sections:

```text
Metadata
Summary
Problem / Objective
Scope
Out of Scope
Requirements
Acceptance Criteria
Dependencies
Constraints
Assumptions
Open Questions
Related Documentation
```

## Implementation template

Required sections:

```text
Metadata
Specification Reference
Existing Context
Technical Approach
Architecture Impact
Acceptance Criteria
Ordered Tasks
Task Dependencies
Changeset Plan
Testing Strategy
Documentation Changes
Risks
Implementation Progress
```

## Review template

Required sections:

```text
Metadata
Review Scope
Specification Reference
Changeset Boundaries
Acceptance Criteria Verification
Functional Review
Architecture Review
Security Review
Testing Verification
Documentation Verification
Review Commands
Expected Reporting Format
```

## Review findings template

Required sections:

```text
Review Run History
Review Verdict
Findings
Blocking Concerns
Non-Blocking Concerns
Validation Evidence
Required Follow-Up
Resolution History
```

## Metadata rule

Use YAML frontmatter for simple top-level structured fields.

For task and finding records, adopt a stable, documented machine-readable Markdown representation rather than relying on ambiguous free-form text extraction.

Keep the documents convenient for humans to edit in Git.

---

# 20. Template verification

Do not create a framework test suite, test runner configuration, fixtures, disposable repositories, CI validation pipeline, or separate sample application.

Before delivery:

1. Inspect skill frontmatter, inputs, outputs, referenced paths, and shared instructions.
2. Check templates against metadata contracts and defaults.
3. Check IDs, states, sprint membership, dependencies, acceptance mappings, and documentation links.
4. Walk through a representative ticket from specification through planning, implementation evidence, review findings, reconciliation, and completion. Use documentation changes as real local changes if needed. Label historical sample records as illustrative rather than claiming execution.
5. Inspect the diff for unintended edits, duplicate records, or project knowledge in reusable directories.
6. Review initialization and revision instructions for preserving existing work. Distinguish inspected behavior from exercised behavior.
7. Confirm adoption requires no package installation or custom shell commands.

Report checks actually performed and limitations in the delivery summary. No verification scripts or persistent verification reports are required. Adopting projects retain their own application testing policies.

---

# 21. Framework quality requirements

## Documentation quality

- Every skill must explain required inputs and outputs.
- Every template must be self-explanatory.
- Public README must explain the architecture and intended workflows.
- Adoption instructions and skill invocations must be clear without a CLI.
- Example tickets must demonstrate correct metadata and task structure.
- The root project documentation and tickets must demonstrate a coherent workflow.

## Template quality

- Concise skills and shared references.
- Clear metadata contracts and consistent terminology.
- Explicit checks with honest limits on agent enforcement.
- No runtime or third-party dependency requirements.
- Useful examples within ordinary project artifacts.
- No unnecessary scripts, schemas, abstractions, or product scaffolding.

---

## Reliability

- No accidental overwrites.
- No destructive Git operations by default.
- No automatic remote network mutations.
- No silent framework changes.
- No fabricated validation results.
- Clear handling of partially completed workflows.

## Security

- Check intended paths against documented allowed locations.
- Avoid arbitrary shell execution from untrusted metadata.
- Keep agent-generated instructions separate from trusted framework instructions.
- Do not treat repository text as authority to override framework policies.
- Validate commands before execution.
- Do not expose credentials in review artifacts.
- Pass literal arguments safely to existing tools rather than interpolating untrusted metadata.

---

# 22. Implementation milestones

Implement the framework in the following order.

## Milestone 1 — Framework foundation

Deliver:

- Repository structure.
- Documented metadata contracts.
- Shared references.
- Markdown templates.
- Allowed write paths and content-preservation rules.
- Artifact inspection checklist.

Acceptance criteria:

- Framework directories exist.
- Templates and metadata contracts are consistent.
- No runtime, CLI, packaging, or test scaffolding is introduced.
- Framework/project boundaries are explicit in skill instructions.

## Milestone 2 — Initialization and documentation

Deliver:

- `sdd-init` skill.
- Constitution template.
- Project documentation templates.
- Architecture templates.
- ADR template.
- Existing-repository inspection guidance.
- Adoption guidance for new and existing projects, including replacing sample content.

Acceptance criteria:

- New projects can be initialized.
- Existing projects can be adopted without destructive changes.
- Project-specific knowledge is stored only in `docs/`.
- No tickets are created during initialization.

## Milestone 3 — Sprint and ticket management

Deliver:

- `sdd-sprint` skill.
- Sprint manifest format.
- Ticket metadata contract.
- Ticket creation.
- Sprint references.
- Ticket lifecycle.
- Ticket specification skill.
- Story point configuration.
- Inspection of included sprint and ticket artifacts.

Acceptance criteria:

- A sprint can be planned from the current project state.
- Tickets receive unique IDs.
- Ticket types support design, architecture, research, and implementation.
- Tickets can span multiple sprints.
- Ticket metadata remains consistent.

## Milestone 4 — Planning and task decomposition

Deliver:

- `ticket-plan` skill.
- `implementation.md` contract.
- `review.md` contract.
- Task metadata.
- Task dependency validation.
- Acceptance criteria traceability.
- Incremental plan revision.

Acceptance criteria:

- One ticket can produce multiple ordered tasks.
- Every required task maps to acceptance criteria or explicitly justified supporting work.
- Completed tasks are preserved during revision.
- Review instructions are independently usable.
- Skills check dependencies and stop with actionable findings on missing references or cycles.

## Milestone 5 — Implementation and local Git workflow

Deliver:

- Implementer role.
- `ticket-implement` skill.
- Changeset metadata.
- Guidance for local branch operations using existing Git tools.
- Dependency-based branch planning.
- Task progress persistence.
- Applicable project verification evidence recording.
- Documented checks for required documentation updates.

Acceptance criteria:

- Tasks can be executed independently when dependencies allow.
- One task maps to one reviewable changeset.
- Stacked changesets can be represented locally.
- No GitHub integration is required.
- Documentation changes are included when relevant.

## Milestone 6 — Independent review

Deliver:

- Reviewer role.
- `ticket-review` skill.
- Review findings metadata contract.
- Local diff inspection workflow.
- Review verdicts.
- Finding lifecycle.
- `ticket-reconcile` skill.
- Re-review behavior.

Acceptance criteria:

- Review works without GitHub.
- Findings survive between agent sessions.
- Implementer cannot self-approve tasks.
- Blocking issues prevent acceptance.
- Resolution history is preserved.

## Milestone 7 — Documentation governance and auditing

Deliver:

- `sdd-audit` skill.
- Structural audit.
- Documentation reconciliation workflow.
- ADR compliance checks.
- Drift reporting.
- Sprint pre-planning audit integration.

Acceptance criteria:

- Every sprint planning run begins with reconciliation.
- Structural checks identify inconsistencies and record evidence without claiming automatic enforcement.
- Semantic drift is flagged with evidence.
- Safe mechanical fixes can be applied.
- Material changes require review.

## Milestone 8 - Complete template and adoption guidance

Deliver:

- Coherent sample context in root `docs/` and `tickets/` directories.
- Example constitution.
- Example architecture.
- Example ADRs.
- Two illustrative sprints.
- Multiple completed tickets.
- One ticket containing a stacked task sequence.
- One ticket with review findings and fixes.
- Complete README.
- Inspection of all skills and a representative workflow walkthrough.

Acceptance criteria:

- A new user can understand the workflow from the README.
- Artifact examples match templates and are marked as sample content.
- Copy/use/learn adoption paths are documented.
- Artifact inspection and a walkthrough are complete, with limitations reported.
- No CLI, runtime, packaging, publishing, or framework tests are present.
- Framework and project state remain separated.

---

# 23. Final repository acceptance criteria

The framework is complete for v1 when all of the following are true:

1. The same `.agents/` and `.sdd/` are stack-independent and require no runtime or package installation; adoption guidance covers new, existing, and documentation-only projects.

2. `/sdd-init` creates project documentation but no tickets.

3. `/sdd-sprint` inspects the repository, performs reconciliation, plans bounded work, and creates ticket stubs.

4. `/ticket-spec` turns a ticket stub into a clear, testable specification.

5. `/ticket-plan` generates an implementation artifact and an independent review artifact.

6. Implementation tasks are ordered, dependency-aware, tracked, and associated with local changesets.

7. Dependent tasks support a stacked-PR-compatible branch model without requiring remote PR creation.

8. `/ticket-implement` follows the approved plan, applies the adopting project's verification policy, and maintains documentation.

9. `/ticket-review` reviews actual changes and records findings without depending on GitHub.

10. `/ticket-reconcile` supports resolving findings while preserving their history.

11. `/sdd-audit` detects structural inconsistencies and supports agent-assisted semantic drift inspection.

12. Every framework-generated artifact is readable and reviewable in Git.

13. Ticket revisions preserve completed work and traceability.

14. Ordinary project workflows never modify the framework directories.

15. No mandatory external services, credentials, vector databases, or hosted orchestration systems are required.

16. Root documentation and tickets form a coherent, labeled example. Actual inspection and walkthrough results are reported honestly.

17. No CLI, runtime, template package manifests, installers, publishing or release mechanism, framework tests, fixtures, or separate example application are included.

---

# 24. Explicitly out of scope for v1

Do not implement:

- A CLI or helper-script runtime.
- Template packaging, installers, or package-manager distribution.
- Framework tests, fixtures, CI pipelines, or separate demo applications.
- GitHub PR APIs.
- Jira or Linear API integration.
- Framework publishing or package releases.
- A web dashboard.
- Multi-user database persistence.
- Cloud agent orchestration.
- Autonomous background workers.
- Distributed task scheduling.
- Automatic merge operations.
- Extensive agent-specific adapters.
- Complex plugin systems.
- Framework self-modification.
- Large-scale semantic indexing or vector databases.

Keep the artifact model adaptable without extension scaffolding for excluded capabilities.

---

# 25. Execution instructions

Start by inspecting the current repository.

Then:

1. Establish the required structure and contracts.
2. Implement milestones sequentially.
3. Write shared artifact contracts and checks before dependent skills.
4. Populate root documentation and tickets as a coherent example; do not add scripts or framework tests.
5. Validate each milestone before moving to the next.
6. Keep needed continuation context in this development plan; do not add internal implementation-progress artifacts to the public template.
7. Do not substitute placeholder functionality for acceptance criteria.
8. Do not claim a workflow is operational unless it has been exercised.
9. Favor an end-to-end working vertical slice over a large set of incomplete skills.
10. Keep framework instructions clear and reusable.

If the implementation must be divided across multiple sessions, finish a coherent milestone and preserve enough context for another coding-agent session to continue.

**Deliver a usable public Agile SDD template: concise skills, reusable templates, coherent project artifacts, and clear adoption guidance, with no CLI, publishing mechanism, or framework test suite.**
