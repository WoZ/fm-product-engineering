# Plugins

This directory holds distributable plugin source packages.

## Packages

| Package | Version | Included workflow |
|---|---|---|
| [FocusMatrix Research and Analysis](fm-research-and-analysis/README.md) (`fm-research-and-analysis`) | `0.1.0` | Clarify exploration input for research brief creation |

## Local Use and Verification

Invoke `$exploration-input-clarification` explicitly with input in chat or a file path. The repository's `.agents/skills/exploration-input-clarification` development symlink points to the canonical skill in this package. Implicit invocation is disabled. See the [package README](fm-research-and-analysis/README.md#local-authoring-and-use) for the relative link and usage details.

Local authoring through the link is separate from installation of the distributable plugin. No marketplace catalog or installation settings are included. Verification is static only; runtime discovery, installation, and behavioral execution have not been verified. Codex is the initial packaging target, and support for other hosts is unverified.

## Adding Packages

Read [Naming](../repository-governance/conventions/naming.md), [Repository layout](../repository-governance/conventions/repository-layout.md), [Skill authoring](../repository-governance/conventions/skill-authoring.md), and [Agent compatibility](../repository-governance/conventions/agent-compatibility.md). These conventions own package placement, identifiers, workflow requirements, and integration policy.
