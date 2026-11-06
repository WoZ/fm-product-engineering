# Changelog

## Unreleased

Initial package version: `0.1.0`.

- Add `exploration-input-clarification` for understanding exploratory requests, confirming intent, and saving clarified input for brief creation.
- Tighten readiness checks for ambiguous subjects and expected outcomes, distinguish unknown intent from choices left open for exploration, and require reasons for deferring material questions. Confirmation does not resolve omitted ambiguities; invocation and input formats remain unchanged.
- Add Codex metadata disabling implicit invocation and a repository-local development symlink to the canonical packaged skill.
- Establish the initial workflow contract; no prior version requires migration. Runtime discovery, installation, and behavioral execution remain unverified. No release has been published or tagged.
