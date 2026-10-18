---
example: true
---
# Platform

## Status and Evidence

Current: a text repository, evidenced by [README](../../README.md), [defaults](../../.sdd/defaults.yaml), and the reusable Markdown files. No application process or deployment exists.

## Responsibilities and Boundaries

The developer's existing agent/editor manages local files. Git history and diffs can supply review boundaries. The template neither installs dependencies nor controls an agent runtime.

## Structure and Data Flow

Files are edited locally and passed between planner, implementer and independent reviewer sessions. Session handoff uses persisted contracts, not hidden conversational context.

## Platform and Dependencies

UTF-8 text and optional local Git capabilities. No build, server, database, package manifest, CI pipeline, publishing target, credentials or hosted service is required. Existing application tooling remains the adopting project's concern.

## Constraints

Skill discovery differs by agent. Explicitly reading a SKILL.md is the fallback; universal slash-command discovery has not been verified. Local filesystem paths and available Git capabilities must be inspected before mutation.

## Decisions and Verification

Inspect [adoption guidance](../development/adoption.md) and [Git rules](../../.sdd/references/task-and-git-model.md). Stack branches in the tickets are illustrative; they do not prove actual history or branch ancestry.
