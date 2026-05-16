---
name: project-dev-governance
description: Organize software project development governance for requirements baselining, pre-development materials, module-level requirement lists, iteration planning, change control, and delivery checkpoints. Use when managing project development, preparing requirement checklists, planning agile iterations, or standardizing project materials for multi-module business systems.
---

# Project Dev Governance

## Overview

Use this skill to turn scattered project inputs into a controlled delivery workflow.
Focus on three things: freeze the right baseline, split development into workable iterations, and keep changes traceable.

## Core Workflow

### 1. Build the baseline first

- Start from the source of truth: bid response, contract, requirements, prototypes, and meeting notes.
- Separate scope into `in scope`, `out of scope`, and `needs change approval`.
- Normalize the project into three layers:
  - module list
  - function groups
  - function points
- If a project has repeated requirement pullback, freeze a baseline before writing the first sprint plan.

Read [references/pre-development-materials.md](references/pre-development-materials.md) when you need the preparation checklist.
Read [references/requirements-template.md](references/requirements-template.md) when you need the requirement document structure.

### 2. Split requirements for development, not for writing

- Do not split only by page.
- Prefer business-domain slicing for management systems:
  - contract / income / invoice / payment
  - execution / work hours / dispatch
  - message / approval / app adaptation
  - security / map / training / reporting
- For each function point, capture:
  - business scene
  - rule and data source
  - permission boundary
  - interface dependency
  - acceptance rule
  - suggested iteration
- If a function point changes formulas, permissions, cross-system sync, or main process, treat it as a change-control candidate.

### 3. Plan iterations with fixed checkpoints

- Use a two-week sprint by default unless the project has a stronger external milestone rhythm.
- For each sprint, define only:
  - sprint goal
  - selected function points
  - interface and testing focus
  - release and acceptance checkpoint
- Use the following control gates:
  - requirement review
  - technical review
  - integration review
  - release review
- Keep development lines parallel when possible:
  - management domain
  - security domain
  - app domain

Read [references/agile-delivery-playbook.md](references/agile-delivery-playbook.md) when you need the project-development agile plan.

### 4. Control requirement churn explicitly

- Do not reject all changes.
- Do not absorb all changes silently.
- Route each new ask into one of three buckets:
  - baseline completion
  - next-sprint candidate
  - formal change request
- Treat these as formal changes by default:
  - new module
  - main-process refactor
  - major statistical formula change
  - new third-party integration
  - permission model redefinition

### 5. Keep only the materials that help delivery control

- This skill is not a generic document-writing bundle.
- Maintain materials that directly support development control:
  - requirement list
  - schedule and sprint breakdown
  - interface confirmation
  - permission matrix
  - formula sheet
  - change log
  - code review summary
  - release note
- If a document does not improve planning, change control, testing, release, or acceptance, do not prioritize it.

## Output Expectations

When using this skill, prefer outputs in this order:

1. A concise scope statement.
2. A structured requirement list.
3. A sprint or milestone breakdown.
4. A change-control view for unstable items.
5. A short risk list.

## Bundled References

- [references/pre-development-materials.md](references/pre-development-materials.md)
  Development preparation checklist and material scope.
- [references/requirements-template.md](references/requirements-template.md)
  Reusable requirement-list template for multi-module projects.
- [references/agile-delivery-playbook.md](references/agile-delivery-playbook.md)
  Simple agile project-development method focused on iteration, change control, and checkpoints.

Keep the skill concise. Put evolving project-specific details into references instead of bloating the main workflow.
