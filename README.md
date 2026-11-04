# FocusMatrix Product Engineering Plugins

An AI-first monorepo for FocusMatrix plugins and skills that help coding agents carry out product engineering workflows. Agents are the primary contributors and consumers of repository instructions; humans review and validate their work.

## Current State

The repository contains governance, documentation, and basic text-file configuration. No plugins have been created or installation-tested. Codex is the initial packaging and validation target. Other coding agents are future targets with unverified compatibility.

## Navigation

- [Agent instructions](AGENTS.md): critical rules and required reading by task.
- [Plugins](plugins/README.md): package placement and the next contribution milestone.
- [Repository governance](repository-governance/README.md): conventions and architectural decisions.

## Contributing

Start with the agent instructions and read the conventions relevant to your change. Provide a concise explanation of the result and verification evidence for human review. No build, validation script, or CI pipeline is configured yet; use the manual checks in the conventions.

The architecture separates portable workflow instructions from host-specific integrations. This is a design goal, not evidence of support for every agent. No license has been selected, and no release or publication is part of this initialization.
