# Optional Deliverables

Read this reference when preparing requested materials. Select the relevant guidance rather than turning every exploration into the whole sequence. Use the user's requested format and language, subject to destination conventions. Include only sections that serve the purpose.

During `Results Consolidation`, apply the [input-alignment review](results-consolidation.md#review-alignment-with-input). Preserve any material departure from the fixed input in the requested result and its saved files; drafting or revising a deliverable never authorizes rewriting input.

## Summary or Decision Record

A compact summary should capture the goal, current approach, accepted decisions and reasons, and consequential open questions. Include rejected alternatives when their tradeoffs help explain a choice. Distinguish proposals from accepted decisions.

When reporting a comparison, preserve the [candidate state and decision boundaries](../SKILL.md#candidate-state-and-decision-boundaries): a locally configured candidate is not necessarily the selected overall approach. Keep relevant open or deferred alternatives and exclusion reasons accurate within the requested result's scope; a limited result does not require a full comparison or additional investigation.

For an architecture decision record or equivalent decision note, put the context, constraints, and assumptions near the beginning. Explain the considered alternatives, meaningful advantages and drawbacks, chosen approach, and rationale. Include consequences and conditions for revisiting the decision when useful. State acceptance status accurately: a request to draft a record does not accept unresolved choices. Use actual dates and known facts rather than copying metadata from an example.

Keep implementation commands out of a decision record unless they are necessary to explain the decision. A decision record explains why; a requested runbook supplies operational detail. If later evidence changes the approach, make the revised decision and its reason clear without inventing approval.

## Diagnostic Collection

Before preparing implementation instructions, determine which facts about the current state are necessary to make them usable. Reuse supplied evidence, checking freshness where it matters. Request only missing checks and decisions; do not demand a complete inventory by default.

When useful, provide commands or a collection script the user can run. Specify the target environment, prerequisites, and what output to return. Collection must read state without changing configuration or deleting data. Disclose any local output-file creation. Avoid collecting credentials or unrelated sensitive information.

Check shell context, quoting, tool versions where relevant, and whether commands rely on shell builtins or external executables. Do not describe a script as tested unless it was exercised. Make partial failures visible so missing evidence is not mistaken for an empty or healthy state.

When results arrive, separate established facts, failed checks, and remaining unknowns. Explain whether a failure blocks the next step and why. Retry only necessary checks. If other evidence establishes the needed fact, continue and explain that basis rather than insisting that every diagnostic command succeed.

## Implementation Instructions

Build instructions from the agreed target and observed current state. Identify consequential unknowns before giving commands that depend on them; use explicit parameters or ask focused questions instead of inventing resource names, limits, or other user decisions. Mark illustrative examples clearly.

Organize the instructions in a workable order. Include prerequisites, execution location, purpose of each meaningful action, commands or concrete actions, and verification with observable success criteria. Explain what to do or where to stop if a prerequisite or check fails. Include relevant destructive consequences, preservation measures, and recovery limitations when the actual operation calls for them.

Separate diagnostic collection from commands that make changes. Respect user constraints such as architecture-only discussion or no commands until requested. Prepared instructions are not execution results; do not claim that the target system was changed or verified by writing them.

When the user reports an error, analyze the specific failure, explain the cause supported by the evidence, and correct the affected instructions. Check whether the correction also changes a prerequisite, later step, or accepted decision. Preserve the rest of the approach when it remains valid. Ask for additional output only when needed to distinguish plausible causes.

## Artifact Review

Before delivery, check that the result reflects current agreements, keeps proposals and unknowns visible, includes the rationale or checks needed for its intended use, and contains no invented successful actions. A complete transcript is a different requested artifact: include only available conversation content, preserve its sequence, and disclose missing material rather than reconstructing it.
