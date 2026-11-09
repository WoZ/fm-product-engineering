# FocusMatrix Product Engineering Plugins

An AI-first monorepo for FocusMatrix plugins and skills that help coding agents carry out product engineering workflows. Agents are the primary contributors and consumers of repository instructions; humans review and validate their work.

## Current State

The repository contains governance, documentation, basic text-file configuration, and the initial [FocusMatrix Research and Analysis package](plugins/fm-research-and-analysis/README.md), version `0.1.0`. Its `exploration-input-clarification` skill prepares confirmed input; `exploration-brief-creation` uses that input to prepare a confirmed brief with a complete research plan. Verification consists of static checks and manual scenario reviews; runtime discovery, installation, and live behavioral execution have not been verified. Codex is the initial packaging and validation target. Other coding agents are future targets with unverified compatibility.

## Local Use

The repository-local `.agents/skills/` symlinks point to the canonical skills inside the plugin. Invoke `$exploration-input-clarification` explicitly with a request in chat or an input file. Invoke `$exploration-brief-creation` with saved clarified input to prepare a brief; it uses default automatic discovery and requires a choice between inspecting existing project materials and Greenfield Zone. Input clarification retains its explicit-only policy. These development links are separate from plugin installation; see the [package README](plugins/fm-research-and-analysis/README.md#local-authoring-and-use) for relative targets and usage details.

## Navigation

- [Agent instructions](AGENTS.md): critical rules and required reading by task.
- [Plugins](plugins/README.md): available package source and local use.
- [Repository governance](repository-governance/README.md): conventions and architectural decisions.

## Contributing

Start with the agent instructions and read the conventions relevant to your change. Provide a concise explanation of the result and verification evidence for human review. No build, validation script, or CI pipeline is configured yet; use the manual checks in the conventions.

The architecture separates portable workflow instructions from host-specific integrations. This is a design goal, not evidence of support for every agent. No license has been selected, and no release or publication has been performed.
