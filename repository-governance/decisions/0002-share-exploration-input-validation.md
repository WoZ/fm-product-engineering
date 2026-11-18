# 0002: Share Exploration Input Validation

Status: Proposed

Date: 2026-11-18

## Context

The clarification workflow evaluates readiness during dialogue. Consuming workflows need to check the saved document using the same requirements, often without the clarification history.

## Decision

Bundle one set of readiness criteria and templates in the research and analysis plugin. Provide a document-only validation skill that returns a pass or fail with actionable problems. Keep dialogue fidelity and user confirmation with the clarification workflow. Consumers check the current document before proceeding.

## Consequences

The installed plugin supplies all shared files. Skills can apply the shared rules directly if separate validation invocation is unavailable. A document explicitly saved as incomplete can be preserved and shared, and its failed readiness check pauses downstream work.
