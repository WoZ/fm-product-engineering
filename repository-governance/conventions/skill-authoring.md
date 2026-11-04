# Skill Authoring

## Purpose and Scope

Define reusable workflows with clear activation boundaries and observable results. Read this convention when changing skills or their supporting resources.

## Rules

- Each skill must have `SKILL.md` with YAML front matter containing `name` and `description`. The name must follow [Naming](naming.md).
- Descriptions must concisely state when to use the skill and any important exclusions. Put discovery information in the description rather than relying on a reader loading the entire workflow first.
- Instructions must define applicability, required inputs and prerequisites, ordered workflow, expected outputs, and completion checks. Describe missing-input and failure handling where they affect the result.
- Prefer instructions over scripts unless deterministic behavior or external tooling is required.
- Keep shared workflow semantics independent of the host. Use [Agent compatibility](agent-compatibility.md) for host-specific metadata and instructions.
- Reference supporting documents explicitly and read them only when the corresponding step needs them. Keep resources within the package under [Repository layout](repository-layout.md).
- State external tool and service prerequisites. Do not assume tools or credentials are available merely because they exist in the author's environment.

## Supporting Resources

Use `references/` for documentation needed while following the workflow, `scripts/` for executable helpers, and `assets/` for resources used in outputs. These directories are optional. Codex metadata may use `agents/openai.yaml`; it is not a substitute for the shared workflow.

The [official skill guide](https://learn.chatgpt.com/docs/build-skills) describes the supported structure and progressive loading.

## Verification

Review a representative matching request, an excluded request, missing required input, and the expected output against the written workflow. Check front matter and resource references manually. When a real skill is introduced, exercise it in Codex and report observed behavior separately from document inspection. See [Change management](change-management.md) for review evidence.
