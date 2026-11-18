# 0002: Solution Exploration Workflow

Status: Accepted

Date: 2026-11-04

## Context

FocusMatrix needs a reusable workflow for investigating UI designs, application architecture, and conventions such as metric names and directory structures. Investigations may require repository analysis, prototypes, test environments, benchmarks, and human or agent evaluation. Their findings inform a later architectural decision record (ADR).

Agents need to resume investigations from saved materials, run individual stages independently, compare alternatives against shared criteria, and distinguish implementation from review. A single long conversation does not provide a sufficient handoff contract for this workflow.

## Decision

Plan the `fm-research-and-analysis` plugin around five skills:

| Skill | Responsibility |
|---|---|
| `solution-exploration` | Coordinate the workflow, maintain investigation state, assign tasks, and synthesize the final recommendation. |
| `exploration-brief` | Initialize the investigation, allocate its ID, collect the user's request, draft the brief, and resolve missing information. |
| `exploration-plan` | Inspect relevant context, identify alternatives, establish comparison criteria, and design experiments. |
| `exploration-build` | Produce alternatives, prototypes, test environments, and experimental evidence when needed. |
| `exploration-review` | Separately evaluate a plan or results against the brief, comparison method, and supporting evidence. |

Support both a coordinated workflow and independent invocation of each specialized skill using an existing investigation directory. Keep UI, architecture, and conventions as domain profiles of the shared workflow. Reuse specialized implementation capabilities where available, with prerequisites declared during implementation.

### Workflow and Review

Allow preliminary repository inspection while clarifying the brief, and return to earlier stages when new findings expose missing requirements. Establish comparison criteria before implementing alternatives. Define completeness relative to the research question and agreed criteria rather than attempting to enumerate every possible solution.

Use the review skill to evaluate comparison methods before costly experiments and to review the resulting artifacts and draft report before completion. A human or another agent performs the separate review; the author's self-check does not replace it. If a separate reviewer is unavailable, retain the results as awaiting review.

The coordinator routes findings to the responsible stage and tracks their resolution. Bound rework by the investigation budget, with two rework cycles after the initial review as the default. If blocking findings remain when that limit is reached, record the unresolved findings and the need for further work without claiming completion. An inconclusive comparison is a valid outcome when supported by sufficient investigation and review.

Reassess affected conclusions and reviews when requirements or artifacts change. Preserve enough version information to identify what was actually reviewed. The final report recommends an alternative, explains tradeoffs and uncertainty, and identifies conditions that could change the recommendation. A later ADR records the final selection, summarizes relevant findings, and links to the retained investigation evidence.

### Execution and Delegation

Separate skill instructions from agent execution. The coordinator controls delegation and follow-up assignments; workers do not create an unrestricted hierarchy of additional agents. Use subagents for bounded research, alternative implementations, and separate review when the host supports them. Keep host-specific integration separate from the portable workflow.

Give each parallel writer a dedicated output area or isolated working tree. Assign one owner to shared documents. Run tasks concurrently only when they do not interfere; comparative benchmarks need controlled conditions rather than simultaneous competition for the same resources. A separate agent does not by itself establish filesystem isolation or guarantee correctness.

### Saved Materials and Handoffs

Store investigation outputs in the target project, independently of the installed plugin. Follow existing project conventions; otherwise use `docs/research/<id>-<topic>/` as the default. The following layout is illustrative and is not an implemented template:

```text
docs/research/<id>-<topic>/
├── exploration.yaml
├── brief.md
├── plan.md
├── report.md
├── options/
│   └── opt-01-<name>/
│       └── option.md
├── experiments/
│   └── exp-01-<name>/
└── reviews/
    └── review-01.md
```

Create optional directories only when needed. Use stable investigation, option, experiment, and review identifiers. Keep workflow state and document references in `exploration.yaml`; use Markdown templates for substantive materials. Store experimental evidence and review records without duplicating them in a separate verification summary.

Define shared templates for the brief, plan, option descriptions, reviews, report, and task handoffs. A handoff identifies its goal, versioned inputs, permitted write area, expected outputs, acceptance criteria, budget, and reasons to return to the coordinator. Review findings identify the affected artifact, unmet criterion, supporting evidence, and closure condition.

Package shared contracts and templates once inside the plugin. Resolve exact schemas, initialization helpers, and domain instructions during implementation. Installed workflows remain independent of this repository's governance files under the existing [repository layout](../conventions/repository-layout.md) and [agent compatibility](../conventions/agent-compatibility.md) conventions.

## Alternatives Considered

- **One skill for the entire workflow:** simpler initially, but provides weaker boundaries for independent stage invocation, resumption, and separate review.
- **One skill for every procedural step:** makes small operations independently addressable, but adds handoffs and duplicated instructions without enough reusable behavior. Directory creation and ID allocation belong to initialization, potentially supported by a small deterministic helper.

## Consequences

The workflow provides reusable stages, explicit ownership, and traceability from the brief through alternatives and evidence to the recommendation. It requires maintaining shared contracts, coordinating writers, and invalidating affected reviews when inputs change. Separate review improves scrutiny but does not guarantee an error-free result.

This decision accepts a planned architecture. No plugin, skill, template, helper, or runtime support is implemented or execution-tested by this record. Implementation validation will cover the three domain profiles, independent stage invocation, cross-agent resumption, incomplete inputs, unavailable tools or reviewers, bounded rework, changed requirements, and initialization without overwriting existing materials.

This record extends the design history after [Repository foundation](0001-repository-foundation.md); it does not supersede that decision or amend repository conventions. Human review of changes to this repository remains governed by [Change management](../conventions/change-management.md), separately from review performed while using the future plugin.
