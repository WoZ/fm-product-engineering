# 0001: Repository Foundation

Status: Accepted

Date: 2026-11-04

## Context

FocusMatrix needs a monorepo for related plugins and skills. Agents are the primary users of instructions, with human review and validation. Codex is the current packaging target, while future agents should be accommodated without duplicating core workflows.

## Decision

Use a root `plugins/` directory for independently versioned packages and `repository-governance/` for policies and architectural history. Keep root AGENTS.md concise and route tasks to conventions instead of loading all rules for every task.

Use portable root plugin manifests, isolate OpenAI-specific integration settings, and retain shared skill instructions once. Plugin identifiers use the `fm-` prefix; skill names omit it and are unique across the monorepo. Use kebab-case for custom paths and American English for repository content.

Initialize documentation and basic text-file configuration only. Keep real plugins, templates, validators, CI, marketplaces, additional integrations, license selection, and release automation deferred. Current policy is owned by the [conventions](../README.md).

## Consequences

Agents can discover relevant rules with limited context, and plugins can grow independently. Portability remains a design property until another host is tested. Codex is the initial target, but installation compatibility is not yet demonstrated because no packages exist. Manual verification is proportionate to this milestone; executable checks and installation evidence will be needed as actual capabilities are introduced.

Repository decision history is distinct from any future plugin for creating decision records. Example package names do not reserve or create plugins.
