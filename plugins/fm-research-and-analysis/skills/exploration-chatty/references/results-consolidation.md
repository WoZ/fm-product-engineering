# `Results Consolidation`

Use this reference when consolidating results against the fixed input. Use the definitions and terminology rules in [the skill's terms](../SKILL.md#terms). Apply it alongside the shared workflow in `SKILL.md`.

Use the [shared question format](../SKILL.md#present-questions) for every question addressed to the user in this phase.

## Phase Logic

Preserve the [validated input baseline](../SKILL.md#input-baseline-and-immutability); result editing cannot change it. Apply the [phase-transition requirements](../SKILL.md#phase-transitions) for readiness and explicit user confirmation before entering another phase.

## Check Selection

Use Request Clarity when interpreting the requested synthesis, delivery, or a qualified confirmation: evaluate Intent, Subject, Scope, and Relationships, retaining material ambiguity as Clarification Required and otherwise Clear. Use Context Consistency And Impact for alignment review: assess Applicable Baseline (the fixed input and accepted research decisions), Revision Boundaries (result edits cannot revise input), Consistency (actual coverage against the task), Dependencies And Impact (affected conclusions), and Evidence For Consequences (support for fulfillment claims). Retain per-criterion findings. Reuse existing findings when still applicable.

These apply the existing checks to consolidation; they do not introduce checks named Input Alignment or Requested Delivery. Treat alignment and delivery requirements as criteria or findings of the applied checks, not new `Phase Agent Check` names. Neither the review nor its diagnostic presentation authorizes additional research or saving.

## Review Alignment with Input

Before delivering the synthesis or saving its files, compare the actual investigation and conclusions with the validated input's goals, mandatory criteria, scope, and source boundaries. Use the retained input, not a reconstructed version reflecting later preferences. Distinguish an actual departure from an unanswered research question, a disclosed evidence limit, or a deliberately limited result allowed by the task.

If a departure is found, explicitly tell the user which original goal or condition is affected, what the investigation actually did or concluded, and how that limits the result. Identify its cause only when supported; otherwise state that it is unknown. Keep factual findings distinct from whether the original task has been fulfilled.

Include the departure and its substance in the requested resulting files, in the user's result language and format. Keep the disclosure with the affected conclusions or limitations so an independently read result cannot imply full compliance. Do not require a separate tracking document, create an unrequested artifact, or copy internal diagnostic terminology into ordinary results. A limited output still preserves a material departure affecting its claims.

Do not rewrite the input, conceal the departure, or present it as a user-approved task change. This review adds no automatic confirmation ceremony or universal completion blocker. Correct the synthesis where possible; if more research or a consequential user choice is genuinely needed, follow the existing stopping and confirmed return-transition rules. If the user stops, stop without adding a procedural question.

## `Phase User Move`

The applicable `Phase User Move` categories and their handling will be defined separately.

## Diagnostic Output

Only while `Debug Mode` is enabled and `Results Consolidation` is active, read [the phase diagnostic instructions](results-consolidation-debug.md). Follow the shared [mode controls and loading rules](../SKILL.md#debug-mode).
