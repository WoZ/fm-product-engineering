# Diagnostic Output for `Topic And Context`

Read this reference only while `Debug Mode` is enabled and `Topic And Context` is active. Use the definitions and terminology rules in [the skill's terms](../SKILL.md#terms), the [shared mode controls](../SKILL.md#debug-mode), and the [phase workflow](topic-and-context.md). This reference defines diagnostic presentation, not additional checks or approval requirements.

## Presentation

Follow the [single active-phase block rule](../SKILL.md#output-boundaries). After a confirmed transition, show only the destination phase's diagnostics; never include the outgoing phase's check list or findings. In Extended output, Agent Actions Taken may briefly record the transition. If no checks were selected for the destination phase yet, use None and Not Applicable with that reason rather than borrowing earlier checks.

After a mode control, follow the [shared redisplay rule](../SKILL.md#redisplay-after-controls): acknowledge the setting, repeat the previous ordinary message, handle any additional substantive input, then show the current diagnostic block. The repeat preserves question identifiers and does not rerun earlier checks or reopen decisions. In extended output, report redisplay as a presentation action; cite any still-pending question separately from a new proposal. When the mode is disabled, redisplay still applies but this diagnostic format does not.

Put the ordinary response and any mode-change acknowledgment before one separate Markdown blockquote headed **`Debug Mode` · Simplified** or **`Debug Mode` · Extended**. Use a `>` prefix for every line, including blank lines, so all diagnostic fields remain in the same block. Do not wrap the rendered block in a code fence or use color-dependent HTML.

Use colored markers only for results: 🟩 for clear or ready findings, 🟨 for clarification, missing evidence, or a Not Ready result, 🟥 for an established conflict or blocker, and ⬜ for a criterion that is not applicable or a selected check not evaluated. Always include the textual status; color alone does not convey the result. A Not Ready result is not automatically an established contradiction.

Use the actual input-submission and validation state. Distinguish a pending document, a usable report for its exact version, and the fixed baseline after PASS. For Phase Transition Readiness, report the shared entry requirements for `Exploration And Refinement`; a document verdict does not confirm the transition.

Present actual questions in the ordinary response using the [shared question format](../SKILL.md#present-questions). In diagnostic `Phase Agent Action Proposal` fields, cite the question identifier and purpose rather than repeating the question or introducing another identifier.

### Readable Layout

- Put each field or section heading in its own paragraph, with a blank blockquote line (`>`) between sections and before and after lists. Do not join multiple fields into one paragraph.
- Under Results, put each check summary in a separate Markdown bullet: `> - 🟩 **Request Clarity — Clear**`. A control-only or no-check explanation is one separate bullet.
- In Extended output, follow Results with a separate bold heading for each evaluated check's criteria. Put every criterion in its own Markdown bullet containing its name, status, and one or two explanatory sentences. Never concatenate criteria in a single paragraph or rely on soft line breaks to separate them.
- Keep Input Interpretation, Agent Actions Taken, and `Phase Agent Action Proposal` as separate labeled sections, with their content in paragraphs below the labels. Keep the comma-separated `Phase Agent Check Set` on its own field line. Preserve the existing field order and level-specific omissions.

## Simplified Level

Include only the heading and these fields, in order:

1. **`Skill Phase`:** `Topic And Context`.
2. **`Phase Agent Check Set`:** Names of the checks selected for the active phase's work in this exchange, separated by commas. Do not list checks merely because they appear in the catalog. Use None for a control-only turn or when no checks were selected for this phase.
3. **Results:** One compact entry per selected check using the result conventions below. Omit input interpretation, criterion details, actions, and `Phase Agent Action Proposal` at this level. For a control-only turn, use ⬜ Not Applicable: Only the diagnostic output setting was handled.

4. **Input Validation:** Separate from `Phase Agent Check Set`, show 🟩 PASS, 🟥 FAIL with a short localized explanation, or ⬜ Not Run / Unavailable with the actual reason. Identify whether the report was obtained this exchange or retained for the same version; do not imply another run occurred. This external verdict is not an additional `Phase Agent Check`.

### Check Result Conventions

- **Request Clarity:** Use 🟩 Clear without explanation, or 🟨 Clarification Required: followed by one or two sentences stating the unresolved subject, intention, scope, or relationship and why it matters.
- **Context Consistency And Impact:** Preserve its per-criterion findings. In the simplified display, use 🟩 Clear without explanation only when those findings contain no relevant unresolved issue. Otherwise use Findings: followed by one or two sentences summarizing the conflict, dependency, missing evidence, or uncertain consequence; select 🟥 for an established conflict or blocker and 🟨 otherwise. Clear and Findings are display summaries, not replacement outcomes or permission to discard the underlying findings.
- **Phase Transition Readiness:** Preserve 🟩 Ready without explanation or 🟨 Not Ready: followed by one or two sentences identifying the missing entry information or blocking gap. Do not relabel these as clarity outcomes.
- If a selected check could not be evaluated, use ⬜ Not Evaluated: and briefly state the dependency. Do not imply that all checks passed because only one was completed.

## Extended Level

Keep the simplified fields and check summaries, adding the following in this order:

1. After `Skill Phase`, add **Input Interpretation:** one paragraph describing the user's understood intentions, their subjects and scope, and consequential ambiguity. Mention applicable classification categories, the submitted source, and whether the user requested validation, rereading, an explanation, or a transition. Do not use this paragraph to reconstruct missing input.
2. After the check summaries, add each evaluated check's criterion results, with a status and one or two sentences per criterion. For Request Clarity, cover Intent, Subject, Scope, and Relationships. For Context Consistency And Impact, cover Applicable Baseline, Revision Boundaries, Consistency, Dependencies And Impact, and Evidence For Consequences. For Phase Transition Readiness, cover Required Entry Information, Blocking Gaps, and Available Working Context. Mark genuinely inapplicable criteria Not Applicable and unresolved or unevaluated criteria honestly. Do not force a consistency finding into Clarification Required when it is a conflict or evidence gap.
3. After criterion results, add **Validation Run:** identify file path or supplied Markdown, the checked version by its retained snapshot (or an available digest), and whether execution used a fresh isolated subagent or a new-chat handoff. Do not require a tracking file. If a run occurred, add **Validator Response:** with the exact final returned report, preserving its wording and language. A nested text fence inside the blockquote may preserve the report; do not fence the entire diagnostic block. This is the returned report, not private reasoning or a tool transcript. A handoff report must be labeled as user-returned rather than a subagent response received here.
4. Add **Token Usage:** report only run-specific usage exposed by the host, preserving distinctions such as input, output, and cached tokens. If unavailable, say Unavailable with the reason; do not estimate, infer from text length, or substitute session totals. User-returned reports normally have no accessible usage metrics. On a control-only or other no-run turn, state No new validation run; do not reproduce an older report or usage as new execution.
5. Add **Agent Actions Taken:** one or two short paragraphs reporting actual responses, corrections, questions, retained or changed decisions, and tool actions where relevant. Distinguish a pending proposal from a completed change. Do not report a rejected or unselected action as performed.
6. Add **`Phase Agent Action Proposal`:** the next interaction actually presented to the user and its intended decision or clarification. If none is needed, state None and the completion, stopping, or control-only reason; do not manufacture a proposal for this field.

## Illustrative Output

After an isolated validator rejects missing source permissions, a simplified block can be:

> **`Debug Mode` · Simplified**
>
> **`Skill Phase`:** `Topic And Context`
>
> **`Phase Agent Check Set`:** Request Clarity
>
> **Results:**
>
> - 🟩 **Request Clarity — Clear**
>
> **Input Validation:** 🟥 FAIL — The current report identifies an unresolved project-source boundary.

The ordinary response explains the reported problem and needed correction in the user's language and waits for corrected input. Extended output also includes the exact returned report and available run metrics, not an invented evaluation of the validator's criteria. If only a diagnostic control was handled, report no new validation and preserve any pending question under its existing identifier.
