---
example: true
---
# AgileSDD project

## Purpose

Help developers organize bounded work through repository-native specifications, plans, implementation evidence, and independent review. Developers can copy the template, use it with a coding agent, or study its artifacts.

## Current Scope

Eight [agent skills](../.agents/skills/sdd-init/SKILL.md) and three roles define the workflow. Reusable templates, references, and defaults live in `.sdd/`. Project docs and ticket examples demonstrate their application. The project has no executable application.

## User Roles

The developer supplies priorities and project decisions. A planner prepares sprint/specification/plan contracts; an implementer executes approved work; an independent reviewer or authorized human verifies it. Role separation does not itself create separate agents.

## Boundaries

No CLI, runtime, dependencies, package installation, publishing mechanism, framework test suite, external integration or remote orchestration is delivered. Application repositories retain their own engineering practices.

## Proposed Work

[T-003](../tickets/T-003/specification.md) illustrates unfinished adoption research. It is not a claim that cross-agent behavior has been executed or verified.
