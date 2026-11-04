# Repository Governance

Conventions are the authoritative repository policies. The root [AGENTS.md](../AGENTS.md) holds critical invariants and routes tasks to the applicable conventions. README files provide navigation; decisions preserve rationale.

## Conventions

| Convention | Read when |
|---|---|
| [Naming](conventions/naming.md) | Creating or renaming paths or identifiers; writing brand references |
| [Repository layout](conventions/repository-layout.md) | Adding repository areas, plugins, or resources |
| [Skill authoring](conventions/skill-authoring.md) | Changing skills and their resources |
| [Agent compatibility](conventions/agent-compatibility.md) | Changing host integration or distribution |
| [Documentation](conventions/documentation.md) | Writing or restructuring documents |
| [Change management](conventions/change-management.md) | Preparing review or changing policy |
| [Versioning and releases](conventions/versioning-and-releases.md) | Changing versions or preparing releases |

## Decisions and Authority

[Repository foundation](decisions/0001-repository-foundation.md) records the initial architecture. Historical decisions do not override current conventions. Repository instructions remain subject to applicable higher-priority instructions and explicit user directions.

For a repository policy conflict, identify the conflicting passages and resolve them explicitly in the change rather than silently inventing an exception. Keep normative requirements in their owning convention. Human reviewers validate changes; agents provide the implementation and verification evidence.
