# Agent Compatibility

## Purpose and Scope

Separate portable workflows from agent-specific integration. Read this convention when changing agent configuration, packaging, or distribution.

## Rules

- Codex is the only initial packaging and validation target. No installed package has been tested at initialization.
- Shared skills must describe workflow semantics without requiring host-specific invocation syntax or tools where a portable description suffices.
- Isolate necessary host-specific metadata and instructions in integration files or clearly identified reference documents. Do not fork entire shared workflows solely for packaging differences.
- Use root `plugin.json` with the supported Agent Plugins schema as canonical plugin metadata. Place OpenAI-specific settings under `extensions.com.openai`; do not maintain a second compatibility manifest initially.
- Add `agents/openai.yaml` only when a skill needs Codex metadata. Add other integrations only when their requirements are concrete.
- Architectural portability does not establish verified support. Before claiming support for another agent, document its packaging, discovery, invocation, and resource behavior and verify a representative installation and workflow.

The [official packaging guide](https://developers.openai.com/plugins/build/plugins) documents root manifests and OpenAI extensions. Recheck the current target format when introducing real packages. [Codex instruction discovery](https://learn.chatgpt.com/docs/agent-configuration/agents-md) explains repository AGENTS.md loading; other hosts' discovery remains unverified.

## Distribution Milestone

When the first usable plugin exists, introduce `.agents/plugins/marketplace.json` if needed for Codex distribution. Entries must reference `./plugins/<plugin-name>` relative to the repository root, not relative to the catalog's directory. Verify paths and installation against the supported Codex client and record the client version and result.

Do not create empty catalogs, agent adapters, MCP configuration, hooks, or local installation settings as part of initialization. Future integrations must follow [Repository layout](repository-layout.md) and [Versioning and releases](versioning-and-releases.md).

## Verification

Inspect the boundary between shared and host-specific content. Check manifest fields and resource paths against current official documentation. Distinguish static format checks from actual installation and workflow execution in all support claims.
