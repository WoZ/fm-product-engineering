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

## Skill Terms

New skills created in this repository should include a `## Terms` section in `SKILL.md` before workflow instructions. This is the default authoring approach; an explicit user opt-out overrides it for the scope the user specifies. Existing skills do not require migration, including during ordinary edits. Adopting this approach for an existing skill is a separate, explicitly scoped change.

### Format and Use

When using this approach:

- Define reusable concepts needed to describe the skill's behavior unambiguously, rather than turning ordinary vocabulary into terms.
- Use a bulleted list with one entry per term: the name in inline code, an em dash, and a clear, unambiguous definition.
- Capitalize the first letter of a single-word term and the first letter of every word in a multiword term.
- Keep definitions in `Terms`; do not duplicate glossaries in references.
- Whenever a defined concept is used in `SKILL.md`, references, or other skill-owned explanatory materials, use its exact term name in inline code delimited by single backticks. Preserve required syntax in code, commands, configuration, exact identifiers, and quotations.
- Usage examples are optional, not a required part of each entry.

Illustrative entries:

- `Proposal` — A suggested option that the user has not yet accepted.
- `Accepted Decision` — A choice explicitly accepted by the user.

### Self-Contained Terminology Instructions

When a skill adopts the `Terms` approach, its `SKILL.md` body must include the following block verbatim, immediately after the term definitions. Do not replace this block with a link to repository conventions or an optional reference.

```markdown
### Terminology Use

Distinguish this skill's defined terms from terminology used for the subject of the task or its results.

- When explaining this skill's workflow choices, debugging its behavior, discussing corrections, or preparing materials about improving or modifying the skill itself, use the relevant terms defined in `Terms`. This lets the user refer to the same unambiguous concepts when requesting changes.
- When referring to a defined concept, use its exact term name in inline code delimited by single backticks. Do not treat ordinary vocabulary as a defined term. Preserve required syntax in code, commands, configuration, exact identifiers, and quotations.
- Do not carry this skill's internal terminology into ordinary recommendations, requests for decisions about the subject, research findings, or resulting documents when they are not about the skill itself.
- If the user requests terminology for an investigation, discussion, or resulting document, introduce an independent vocabulary for that subject or result. Such a request does not imply using or inheriting this skill's `Terms`.

Apply this distinction by subject, regardless of delivery format, including chat, saved documents, and corresponding portions of templates. A template's workflow guidance uses this skill's terms; its output content follows the terminology of the intended result.
```

## Supporting Resources

Use `references/` for documentation needed while following the workflow, `scripts/` for executable helpers, and `assets/` for resources used in outputs. These directories are optional. Codex metadata may use `agents/openai.yaml`; it is not a substitute for the shared workflow.

The [official skill guide](https://learn.chatgpt.com/docs/build-skills) describes the supported structure and progressive loading.

## Verification

Review a representative matching request, an excluded request, missing required input, and the expected output against the written workflow. Check front matter and resource references manually. When a real skill is introduced, exercise it in Codex and report observed behavior separately from document inspection. See [Change management](change-management.md) for review evidence.
