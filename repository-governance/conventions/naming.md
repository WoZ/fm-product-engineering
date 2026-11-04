# Naming

## Purpose and Scope

Define names for repository paths, plugin identifiers, and skill identifiers, and distinguish them from brand names in prose. Read this convention before creating or renaming identifiers or paths, or writing brand references.

## Rules

- Custom file stems and directory names must use lowercase ASCII kebab-case: words of letters or digits separated by single hyphens. Do not use spaces, underscores, or leading or trailing hyphens.
- Plugin identifiers must start with `fm-` followed by a descriptive kebab-case name. They must be unique across the repository.
- Skill identifiers must use descriptive kebab-case without the organization prefix `fm-`. They must be unique across all plugins in the monorepo. Domain prefixes such as `rfd-` may clarify their purpose.
- A plugin directory must match its manifest `name`; a skill directory must match its SKILL.md front matter `name`.
- Use `repository-governance` for repository policy and decision history.
- Check names against the target format's current length and syntax restrictions before introducing a package.

## Brand Names in Prose

- `FM` stands for FocusMatrix. Use `FocusMatrix` for the brand on first mention in a document; `FM` may be used for subsequent mentions. In README titles and introductory descriptions, use `FocusMatrix` when naming the brand.
- Lowercase `fm` is for technical names, such as the `fm-` plugin prefix and the repository directory `fm-product-engineering`. Do not use it as the brand name in prose. Preserve exact spelling when quoting paths, identifiers, filenames, or other technical names, and format them as code.

## Exceptions and Examples

Standard filenames retain exact spelling: `AGENTS.md`, `SKILL.md`, `README.md`, `CHANGELOG.md`, and a future `LICENSE`. Configuration filenames such as `.editorconfig`, `.gitattributes`, `.gitignore`, `plugin.json`, `marketplace.json`, and `agents/openai.yaml` follow their tools' requirements. New tool-defined exceptions must be documented here when introduced.

Decision filenames use a four-digit sequence and descriptive stem, such as `0001-repository-foundation.md`. Ordinary documentation uses names such as `skill-authoring.md`.

`fm-research-and-analysis` is an illustrative plugin name; `rfd-brief-creation` is an illustrative skill name. Neither example establishes a real package.

## Verification

Inspect new paths and identifiers, compare names with manifests, and search all existing skills for collisions. Treat renames as compatibility changes under [Versioning and releases](versioning-and-releases.md). See [Repository layout](repository-layout.md) for placement.
