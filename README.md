# AgileSDD

A public template for Agile Spec-Driven Development. Copy it into a project, use its coding-agent skills, or follow its example tickets to learn the workflow.

Everything is Markdown and YAML. There is no CLI, package installation, runtime, publishing mechanism, or framework test suite. Your application keeps its own build and testing practices.

## Start a project

1. Use this repository as a template, or copy its files into a new repository.
2. Keep `.agents/` and `.sdd/`. Replace the sample `docs/` and `tickets/` content with your own project knowledge and history. Inspect before removing anything; in an existing project, preserve its documentation and tickets and copy only the reusable directories initially.
3. Ask your coding agent to use `.agents/skills/sdd-init/SKILL.md`, supplying your product purpose and known constraints. Initialization creates documentation and a ticket guide; it creates no tickets or sprints. On an empty project, explicitly say that there is no implemented application yet.
4. Ask for a bounded sprint, then specify, plan, implement, and independently review one ticket at a time.

The [development plan](development-plan.md) explains how this template was authored; adopting projects do not need to copy it. No installer or remote action is involved. In a Python or TypeScript repository, initialization reads its existing manifests/source/checks; the template introduces no Python or Node dependency. A documentation-only project uses content inspection and link checks.

## Invoke a skill

Skill discovery varies by coding agent. Use its skill picker or supported invocation syntax. If it does not discover `.agents/skills`, explicitly ask it to read the relevant `SKILL.md` and follow its repository-relative references. `$skill-name` and `/skill-name` below are agent conventions, never shell commands.

| Request | Skill | Result |
|---|---|---|
| Adopt SDD in this repository | [sdd-init](.agents/skills/sdd-init/SKILL.md) | Baseline project docs, no tickets |
| Plan one sprint toward this goal | [sdd-sprint](.agents/skills/sdd-sprint/SKILL.md) | Reconciliation, sprint proposal, then approved stubs |
| Specify T-001 | [ticket-spec](.agents/skills/ticket-spec/SKILL.md) | Requirements and acceptance criteria |
| Plan T-001 | [ticket-plan](.agents/skills/ticket-plan/SKILL.md) | Tasks and independent review contract |
| Implement T-001, optionally TASK-001 | [ticket-implement](.agents/skills/ticket-implement/SKILL.md) | Ready work, evidence and documentation |
| Review T-001 in a fresh session | [ticket-review](.agents/skills/ticket-review/SKILL.md) | Findings, verdict and eligible acceptance |
| Address findings for T-001 | [ticket-reconcile](.agents/skills/ticket-reconcile/SKILL.md) | Fixes and re-review handoff |
| Audit the current sprint | [sdd-audit](.agents/skills/sdd-audit/SKILL.md) | Evidence-backed consistency/drift findings |

For example: "Use the sdd-sprint skill to plan one sprint improving our search filters. Reconcile the current implementation and open work before proposing tickets." Review the resulting scope before approving it. Existing authorization counts when it covers the actual decision; the workflow should not repeatedly ask for the same approval.

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
