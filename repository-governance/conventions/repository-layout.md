# Repository Layout

## Purpose and Scope

Keep repository governance separate from distributable packages. Read this convention when adding areas, plugins, or resources.

## Rules

- Root `plugins/` must contain one directory per distributable plugin.
- Root `repository-governance/conventions/` must contain repository policies; `repository-governance/decisions/` must contain architectural rationale.
- Root `AGENTS.md` must remain a concise router, targeting no more than 60 lines. Add nested instruction files only through a deliberate policy change when distinct local rules are needed.
- Create optional directories only when they contain useful resources. A README may preserve an otherwise empty meaningful directory in Git.

## Future Package Contract

The following tree is illustrative; it does not describe an existing plugin:

```text
plugins/<plugin-name>/
├── plugin.json
├── README.md
├── CHANGELOG.md
└── skills/
    └── <skill-name>/
        ├── SKILL.md
        ├── references/       # Optional documentation
        ├── scripts/          # Optional executable resources
        ├── assets/           # Optional output resources
        └── agents/
            └── openai.yaml  # Optional Codex metadata
```

A skill-based plugin must include at least one usable skill. Keep portable identity in root `plugin.json` using the supported Agent Plugins schema. Root package resources may be added when actually required. See [Agent compatibility](agent-compatibility.md) for host-specific settings and the official format reference.

Each installed plugin must work independently of the source repository. Referenced runtime resources must be packaged inside it; do not rely on repository governance, undeclared sibling plugins, source checkout paths, or symlinks escaping the package. Declare external tool or service prerequisites explicitly rather than treating them as bundled files.

## Verification

Inspect package references from the installed-package perspective. Confirm every bundled resource exists within the package and every external prerequisite is declared. Confirm examples have not become empty packages. Apply [Naming](naming.md) and [Skill authoring](skill-authoring.md) when adding content.
