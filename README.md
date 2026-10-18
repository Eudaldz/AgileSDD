# AgileSDD

A public template for Agile Spec-Driven Development. Copy it into a project, use its coding-agent skills, or follow its example tickets to learn the workflow.

Everything is Markdown and YAML. There is no CLI, package installation, runtime, publishing mechanism, or framework test suite. Your application keeps its own build and testing practices.

## Start a project

1. Use this repository as a template, or copy its files into a new repository.
2. Keep `.agents/` and `.sdd/`. Replace the sample `docs/` and `tickets/` content with your own project knowledge and history. Inspect before removing anything; in an existing project, preserve its documentation and tickets and copy only the reusable directories initially.
3. Ask your coding agent to use `.agents/skills/project-init/SKILL.md`, supplying your product purpose and known constraints. Initialization creates documentation and a ticket guide; it creates no tickets or sprints. On an empty project, explicitly say that there is no implemented application yet.
4. Ask for a bounded sprint. Specify each ticket once, then repeat plan → implement → independent review, returning to human-led planning whenever review requests another iteration.

The [development plan](development-plan.md) explains how this template was authored; adopting projects do not need to copy it. No installer or remote action is involved. In a Python or TypeScript repository, initialization reads its existing manifests/source/checks; the template introduces no Python or Node dependency. A documentation-only project uses content inspection and link checks.

## Invoke a skill

Skill discovery varies by coding agent. Use its skill picker or supported invocation syntax. If it does not discover `.agents/skills`, explicitly ask it to read the relevant `SKILL.md` and follow its repository-relative references. The slash commands below are agent skill invocations, never shell commands.

| Request | Skill | Result |
|---|---|---|
| Adopt SDD in this repository | [project-init](.agents/skills/project-init/SKILL.md) | Baseline project docs, no tickets |
| Plan one sprint toward this goal | [project-sprint](.agents/skills/project-sprint/SKILL.md) | Reconciliation, sprint proposal, then approved stubs |
| Specify a ticket | [ticket-spec](.agents/skills/ticket-spec/SKILL.md) | Requirements and acceptance criteria |
| Plan a ticket iteration | [ticket-plan](.agents/skills/ticket-plan/SKILL.md) | Human direction, finding assessment, exact changes and review contract |
| Implement the approved iteration | [ticket-implement](.agents/skills/ticket-implement/SKILL.md) | Planned changes, evidence and documentation |
| Review a ticket in a fresh session | [ticket-review](.agents/skills/ticket-review/SKILL.md) | Findings, verdict and eligible acceptance |
| Audit the current sprint | [project-audit](.agents/skills/project-audit/SKILL.md) | Evidence-backed consistency/drift findings |

### Human decisions drive the work

Humans own the specification: the problem worth solving, intended behavior, scope, constraints, and what counts as success. Humans also own the engineering decisions and tradeoffs in the plan. The agent structures that input, checks it against the repository, proposes missing details, and exposes unanswered questions. It must not turn guesses into requirements or approved decisions. Read and correct the resulting specification and plan before approving them; a polished document is not evidence that it describes the right work.

Write and approve the specification once per ticket; its requirements and acceptance criteria remain fixed through implementation iterations. Changed product requirements belong in a separately authorized linked ticket. Drafting the specification can take several conversations; “once” means one stable contract, not one message.

Every iteration starts with human-led planning. Provide written instructions or ask the agent to interview you about priorities, constraints and tradeoffs. After review, explain what matters, what does not, and where you disagree. The planner checks each finding's evidence, validity and scope against the fixed specification, records proposed actions, and writes the exact iteration changes in Markdown. Optional improvements can be deferred; verified acceptance failures cannot be dismissed as out of scope. Review the plan before execution.

Implementation and review use those recorded decisions and should almost never need human questions. Unforeseen conflicts or missing authority are exceptions: record the blocker and return affected work to planning. Existing authorization counts when it covers the actual iteration decisions; approval of a prior plan does not automatically authorize different work.

### Prompt examples

Each skill has one example below. They use a product catalog scenario to show the decisions a human supplies, not defaults the skills should impose. Replace `<ticket>` with your actual ticket identifier or artifact path; no particular identifier or ticket number is required by these prompts.

**Initialize project context: supply the product purpose and engineering constraints.**

```text
/project-init
We maintain a spare-parts catalog for repair shops. Mechanics use it on phones to find compatible parts; stock and pricing come from our existing inventory service. This repository already has a React frontend and a Python API backed by PostgreSQL. Inspect the code to confirm the details.

Document the current system, preserving our existing docs and tickets. Our constraints: no new hosted services, no changes to inventory ownership, and keyboard-accessible customer flows. The inventory service is outside this repository. Ask me about missing product or ownership decisions rather than inventing them.
```

**Plan a sprint: choose the outcome, priorities, and capacity.**

```text
/project-sprint
Plan one sprint improving catalog search filters. Shop staff report that they cannot share a filtered result with a colleague and lose their selections when returning from a product page.

We have two developers for one week, with one day each reserved for support. Prioritize shareable filter URLs and reliable back navigation. Defer saved searches, analytics, and new filter types. Reconcile the implementation and open work first; propose a smaller scope if this does not fit. I will review the proposed scope before we commit to it.
```

**Specify a ticket: define the actual behavior and acceptance examples.**

```text
/ticket-spec
Specify <ticket> for shareable catalog filters. A mechanic must be able to copy the current URL and send it to a colleague who sees the same selected filters after opening it.

Include category, brand, and in-stock filters. Multiple brands mean OR; different filter groups combine with AND. Apply changes immediately, reset pagination to page 1, and preserve the search text and sort order. Reload and browser Back/Forward must restore the selections. Clear filters removes those three filter groups but keeps search and sort. Do not add saved searches or change the search API's matching rules.

Acceptance example: select category Brakes, brands A and B, and in-stock only. Opening the copied URL in a new session must restore those controls and request in-stock brake parts from either brand. Returning from a product page must restore that same state.

Ignore unknown query parameters without crashing or dropping them from the URL. I have not decided how to handle a brand value that no longer exists: show me the current behavior and the options before finalizing that requirement. Structure these decisions into the specification, identify other gaps, and leave it pending my review.
```

**Plan an iteration: provide engineering direction and context for assessing review findings.**

```text
/ticket-plan
Plan the next iteration for <ticket> against its fixed approved specification and latest review. Back/Forward restoring stale selections is a release blocker: reproduce it and plan a correction. The review also proposes saved filter presets; those are explicitly excluded from this ticket. Assess each finding against the spec and actual code, explain which are valid and in scope, and record a proposed disposition for the rest without erasing them.

Keep the URL as the source of truth and reuse our router and query parser. No new state-management dependency, API endpoint, migration, or saved-search feature. Keep the correction focused on URL synchronization and use our existing browser tests to cover Back/Forward and returning from a product page. Preserve the accepted parsing work unless evidence shows it is part of the defect.

Old bookmarked URLs must keep working. Ask me concrete questions about any unresolved compatibility or scope tradeoffs before finalizing; do not guess. Write the exact changes, exclusions, checks and review handoff for this iteration, retain the previous plan and review history, and leave the new plan for my approval.
```

**Implement a ticket: the approved iteration supplies the instructions.**

```text
/ticket-implement
<ticket>
```

**Review a ticket: run in a fresh independent session using the recorded review boundary.**

```text
/ticket-review
<ticket>
```

**Audit: identify the scope and the concern that needs investigation.**

```text
/project-audit
Audit the active sprint's catalog-search tickets and docs/architecture/ against the current implementation. We recently moved filter parsing into the router, but I suspect the architecture docs still describe component-local state and some tickets may claim completion without navigation checks. Report evidence and affected records so I can decide what to correct or schedule; do not rewrite product decisions to match the code.
```

The flow is **spec once → plan → implement → review → plan → implement → review** until independent review approves and completion gates pass. The planning example shows a later iteration; the first uses the same skill with human direction and no prior findings. Every requested-change cycle returns to planning before implementation. Plans preserve earlier scope, decisions and approvals; finding proposals remain pending independent verification.

## Where information lives

| Path | Contents | Change during normal project work? |
|---|---|---|
| `.agents/skills/` and `.agents/roles/` | Reusable workflow behavior and roles | No |
| `.sdd/templates/`, `.sdd/references/`, `.sdd/defaults.yaml` | Reusable formats, contracts and defaults | No |
| `docs/` | Your project constitution, context, architecture, decisions and overrides | Yes |
| `tickets/` | Your sprint and ticket history | Yes |
| Your application paths | Code, configuration, application tests | Only within the approved task scope |

The specification owns ticket metadata. Sprint manifests own membership. Plans own tasks; review runs own findings. Conflicts are reported and reconciled, not silently overwritten. Put project workflow overrides in [docs/workflow.md](docs/workflow.md), never in reusable defaults. See the [artifact contracts](.sdd/references/artifact-contracts.md) for formats and allowed writes.

## Follow the example

This repository uses its own documentation as a small project example. [docs/README.md](docs/README.md) indexes current architecture and decisions; [tickets/README.md](tickets/README.md) indexes two illustrative sprints.

1. Read [T-001's specification](tickets/T-001/specification.md), then its plan and review contract. It establishes a documentation baseline.
2. Read [T-002's implementation](tickets/T-002/implementation.md). Two tasks form a local branch stack; the second depends on the first's deliverable.
3. Read [T-002's findings](tickets/T-002/review-findings.md). A missing preservation rule is reported, acknowledged, fixed, and independently rechecked without erasing the original verdict.
4. Read [T-003](tickets/T-003/specification.md) to see unfinished research carried into a later sprint with the same identity.

Every sample ticket, sprint, approval, review identity, and branch is illustrative. These records do not claim real reviews, human decisions, Git objects, or executed historical commands. The actual files are readable examples; a fresh project replaces their state instead of inheriting their approvals or completed statuses.

## Work and review separately

The implementer follows an approved, current plan and records actual checks. A fresh reviewer session or an authorized human checks the specified boundary. One session changing role labels is not independent review. If no reviewer is available, leave acceptance pending and hand off the review contract; do not invent approval. Skills do not imply permission to spawn agents or create remote resources.

Tasks can use local branches and dependent stacks without a hosting account. If Git is unavailable, choose working-tree mode in your project workflow and identify a stable review snapshot. See the [task/Git model](.sdd/references/task-and-git-model.md). Branch creation, commits and other mutations follow the user's authorization; no push, merge, publication or release is part of this template.

The contracts guide an agent or human; no executable validator or sandbox enforces them. Inspect actual diffs, record unavailable checks, and use your project's appropriate verification. See [adoption and use](docs/development/adoption.md) for reruns, revisions, and handoffs.
