# Changelog

## Unreleased

Initial package version: `0.1.0`.

- Make clarification blockers require an internal check of competing meanings, unavoidable assumptions, and whether a faithful handoff can preserve uncertainty. Require a concrete reason for reclassifying gaps or correcting readiness; a request for more questions alone does not change their status. Invocation, version, and output structure remain unchanged.
- Add user-controlled deepening rounds with dynamically derived clarification categories, a checkpoint after every round, and a finish-or-continue choice even when input is already ready. Optional clarification does not block readiness; stopping with blockers does not save a final artifact. Choosing to finish and confirming the final restatement remain separate interactions. Existing dialogue drivers must handle these new checkpoints; the development evaluation has not been adapted. Invocation, version, and output structure remain unchanged.
- Add packaged Codex interaction guidance for available native question tools and a text fallback, without changing client settings or requiring a question tool. Verify the written transitions through manual scenario walkthroughs; live UI behavior remains unverified.
- Add `exploration-input-clarification` for understanding exploratory requests, confirming intent, and saving clarified input for brief creation.
- Tighten readiness checks for ambiguous subjects and expected outcomes, distinguish unknown intent from choices left open for exploration, and require reasons for deferring material questions. Confirmation does not resolve omitted ambiguities; invocation and input formats remain unchanged.
- Breaking output contract change: standardize clarified input as self-contained Markdown using a bundled template with a descriptive H1, fixed English section names, and conditional content categories. Remove the required original-input handoff and separate brief-preparation question list. Consumers must use the current meaning incorporated into the document instead of reconstructing intent from source history or expecting a brief-question list. Readiness, confirmation, saving, invocation, and input formats remain unchanged; no released artifacts are rewritten.
- Add Codex metadata disabling implicit invocation and a repository-local development symlink to the canonical packaged skill.
- Establish the initial workflow contract; no prior version requires migration. Runtime discovery, installation, and behavioral execution remain unverified. No release has been published or tagged.
