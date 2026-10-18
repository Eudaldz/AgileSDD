# Tasks, dependencies, and local Git

## Ready work

Task IDs are unique within a ticket. Before planning or selecting work, verify every dependency exists, no task depends on itself, and ticket-level dependencies refer to existing tickets. Check cycles at both levels: repeatedly remove nodes with no remaining predecessors, breaking ties by numeric ID. If nodes remain with none removable, report the cycle and block selection. This stable topological order is the display/execution order; it does not create dependencies between unrelated tasks.

Ticket dependencies must be accepted or done before implementation unless a reviewed plan records the partial-deliverable dependency and evidence. Task predecessors must reach `task_ready_after`: `implemented` permits implemented/in_review/accepted predecessors, while `accepted` requires accepted. A blocked, cancelled, or pending predecessor is never satisfied. Recheck predecessor review findings before starting dependent work; blocking findings invalidate readiness. Mark only ready work as ready. Unrelated tasks can proceed independently, but do not delegate without applicable user authorization.

## Changeset boundary

One task maps to one logical reviewable changeset, possibly several commits. Record paths, actual base commit, branch/base branch, commit IDs when present, review state, and verification evidence in that task. Documentation belongs in its related changeset. Research with no meaningful diff records its findings as a deliverable and an exception; never create an empty commit or PR solely for bookkeeping.

Before branch operations inspect `git status --short`, the current branch, and the proposed base. Never reset, clean, stash, switch away from dirty work, rewrite history, merge, push, or discard content without the necessary authorization. Ask only when an operation actually requires new authorization; existing authorization persists. If unrelated changes prevent a clean boundary, stop branch work and propose an isolated checkout or a documented working-tree boundary. No remote actions are implied by skill invocation. Without Git, use `git.mode: working-tree` and clearly state the limits on independent diff verification.

## Local stack

For independent tasks branch from the approved project base. A dependent task may branch from its single predecessor's task branch:

```text
main
  ticket/T-001/task-001
    ticket/T-001/task-002
      ticket/T-001/task-003
```

A dependency on several branches requires an explicit integration/base decision in the plan. Do not arbitrarily choose one predecessor or merge branches automatically. Inspect the base for the actual needed changes. Record the dependency and selected base; names alone do not prove ancestry. Prefer task-only diffs (`base...branch`) and confirm they exclude unrelated changes. With already integrated predecessors, a task can base on the updated project branch instead.

Do not create branches just because a plan describes them. Commit/branch creation follows the user's repository permissions. In working-tree mode record exact paths and capture a diff/snapshot with an identifiable boundary using the environment's existing capabilities before review. If that is unavailable, mark the review blocked rather than inventing commit IDs. External PR links are optional metadata; this template provides no remote PR or publication mechanism.

## Repeatable inspection

Use existing Git commands where available: `git status --short`, `git diff --check`, `git diff -- <literal-path>`, `git diff --cached -- <literal-path>`, `git log`, and `git show`. Include untracked files explicitly; ordinary `git diff` omits them. Substitute inspected literal arguments safely. Before using `base...branch`, verify both refs and inspect the merge-base. Record exact commands, outcomes, and checks not run. A branch name or claimed successful test is not verification evidence.
