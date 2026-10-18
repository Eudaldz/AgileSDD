---
ticket_id: "{{T-nnn}}"
---
# Review findings: {{T-nnn}}

## Review Run History

{{append R-nnn with reviewer identity, scope, spec/plan revisions, immutable boundary, checks/outcomes, limitations, and verdict; no review has occurred until recorded}}

## Review Verdict

{{latest run ID and verdict, or not reviewed; prior runs remain historical}}

## Findings

<!-- Add a mapping only when a real finding exists. Remove this sample mapping when unused. -->
### F-001

```yaml
id: F-001
task_id: null
severity: major
category: "{{category}}"
description: "{{actionable defect}}"
evidence: "{{observed behavior or diff, not assumption}}"
files: []
suggested_resolution: "{{concrete next action}}"
status: open
introduced_in: R-001
resolution: null
history:
  - run: R-001
    actor: "{{reviewer}}"
    action: opened
    evidence: "{{observation}}"
```

## Blocking Concerns

{{unresolved critical/major findings, missing evidence, or none}}

## Non-Blocking Concerns

{{minor/suggestion disposition or follow-up}}

## Validation Evidence

{{actual check results, exact scope, and checks not run}}

## Required Follow-Up

{{for changes_requested: hand off to human-led ticket-plan with the findings before any implementation; for blocked: identify evidence/authority needed; otherwise owners, review reruns, or none}}

## Resolution History

{{append resolution proposals and reviewer verification; retain original findings and every previous verdict}}
