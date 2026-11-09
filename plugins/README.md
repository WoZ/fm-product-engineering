# Plugins

This directory holds distributable plugin source packages.

## Packages

| Package | Version | Included workflow |
|---|---|---|
| [FocusMatrix Research and Analysis](fm-research-and-analysis/README.md) (`fm-research-and-analysis`) | `0.1.0` | Clarify exploration input and prepare confirmed research briefs with complete research plans |

## Local Use and Verification

Invoke `$exploration-input-clarification` explicitly with input in chat or a file path. Then use `$exploration-brief-creation` with saved clarified input to prepare a brief; this new skill uses default automatic discovery. The repository's `.agents/skills/` development symlinks point to the canonical packaged skills. Input clarification remains explicit-only. See the [package README](fm-research-and-analysis/README.md#local-authoring-and-use) for relative links and usage details.

Local authoring through the links is separate from installation of the distributable plugin. No marketplace catalog or installation settings are included. Verification consists of static checks and manual scenario reviews; runtime discovery, installation, and live behavioral execution have not been verified. Codex is the initial packaging target, and support for other hosts is unverified.

## Adding Packages

Read [Naming](../repository-governance/conventions/naming.md), [Repository layout](../repository-governance/conventions/repository-layout.md), [Skill authoring](../repository-governance/conventions/skill-authoring.md), and [Agent compatibility](../repository-governance/conventions/agent-compatibility.md). These conventions own package placement, identifiers, workflow requirements, and integration policy.
