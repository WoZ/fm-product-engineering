# FocusMatrix Product Engineering Plugins

An AI-first monorepo for FocusMatrix plugins and skills that help coding agents carry out product engineering workflows. Agents are the primary contributors and consumers of repository instructions; humans review and validate their work.

## Current State

The repository contains governance, documentation, basic text-file configuration, and the initial [FocusMatrix Research and Analysis package](plugins/fm-research-and-analysis/README.md), version `0.1.0`. Its `exploration-input-clarification` skill prepares confirmed input for research brief creation. Verification is static only; runtime discovery, installation, and behavioral execution have not been verified. Codex is the initial packaging and validation target. Other coding agents are future targets with unverified compatibility.

## Local Use

The repository-local `.agents/skills/exploration-input-clarification` symlink points to the canonical skill inside the plugin. Invoke it explicitly as `$exploration-input-clarification`, supplying the request in chat or identifying an input file. Implicit invocation is disabled by Codex metadata. This development link is separate from plugin installation; see the [package README](plugins/fm-research-and-analysis/README.md#local-authoring-and-use) for the relative target and usage details.

## Navigation

- [Agent instructions](AGENTS.md): critical rules and required reading by task.
- [Plugins](plugins/README.md): available package source and local use.
- [Repository governance](repository-governance/README.md): conventions and architectural decisions.

## Contributing

Start with the agent instructions and read the conventions relevant to your change. Provide a concise explanation of the result and verification evidence for human review. No build, validation script, or CI pipeline is configured yet; use the manual checks in the conventions.

The architecture separates portable workflow instructions from host-specific integrations. This is a design goal, not evidence of support for every agent. No license has been selected, and no release or publication has been performed.
