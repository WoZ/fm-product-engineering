# Repository Governance

Conventions are the authoritative repository policies. The root [AGENTS.md](../AGENTS.md) holds critical invariants and routes tasks to the applicable conventions. README files provide navigation; decisions preserve rationale.

## Conventions

| Convention | Read when |
|---|---|
| [Naming](conventions/naming.md) | Creating or renaming paths or identifiers; writing brand references |
| [Repository layout](conventions/repository-layout.md) | Adding repository areas, plugins, or resources |
| [Skill authoring](conventions/skill-authoring.md) | Creating or changing skills and their resources, including [skill terms](conventions/skill-authoring.md#skill-terms) |
| [Agent compatibility](conventions/agent-compatibility.md) | Changing host integration or distribution |
| [Documentation](conventions/documentation.md) | Writing or restructuring documents |
| [Change management](conventions/change-management.md) | Checking consistency for any change, preparing a review, or changing repository policy. See the [skill terminology check](conventions/change-management.md#skill-terminology-consistency-check) when editing a skill that uses `Terms` or its supporting resources. |
| [Versioning and releases](conventions/versioning-and-releases.md) | Changing versions or preparing releases |

## Decisions and Authority

[Repository foundation](decisions/0001-repository-foundation.md) records the initial architecture. [Solution exploration workflow](decisions/0002-solution-exploration-workflow.md) records the planned research skills, coordination model, and saved investigation materials.

Historical decisions do not override current conventions. Repository instructions remain subject to applicable higher-priority instructions and explicit user directions.

Follow [Change management](conventions/change-management.md#consistency-check-for-every-change) to report policy conflicts and address those within the scope of the change. Keep normative requirements in their owning convention. Agents provide the implementation and verification evidence for human review.
