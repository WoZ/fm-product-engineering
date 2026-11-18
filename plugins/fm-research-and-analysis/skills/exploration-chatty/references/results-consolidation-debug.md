# Diagnostic Output for `Results Consolidation`

Read this reference only while `Debug Mode` is enabled and `Results Consolidation` is active. Use the definitions and terminology rules in [the skill's terms](../SKILL.md#terms), the [shared mode controls](../SKILL.md#debug-mode), and the [phase workflow](results-consolidation.md). Use the phase guidance's check selection for actual consolidation work; do not invent check names to fill the display.

## Presentation

Follow the [single active-phase block rule](../SKILL.md#output-boundaries). After a confirmed transition, show only the destination phase's diagnostics; never include the outgoing phase's check list or findings. In Extended output, Agent Actions Taken may briefly record the transition. If no checks were selected for the destination phase yet, use None and Not Applicable with that reason rather than borrowing earlier checks.

After a mode control, follow the [shared redisplay rule](../SKILL.md#redisplay-after-controls): acknowledge the setting, repeat the previous ordinary message, handle any additional substantive input, then show the current diagnostic block. The repeat preserves question identifiers and does not rerun earlier checks or reopen decisions. In extended output, report redisplay as a presentation action; cite any still-pending question separately from a new proposal. When the mode is disabled, redisplay still applies but this diagnostic format does not.

Put the ordinary result and any mode-change acknowledgment before a separate Markdown blockquote headed **`Debug Mode` · Simplified** or **`Debug Mode` · Extended**. Prefix every diagnostic line, including blank lines, with `>`. Keep the diagnostic block outside the resulting document or saved artifact unless the user specifically requests its inclusion. Do not wrap the rendered block in a code fence or use color-dependent HTML.

Use colored markers only for results: 🟩 for clear or ready findings, 🟨 for clarification or missing information, 🟥 for an established conflict or blocker, and ⬜ for an inapplicable criterion or a selected check not evaluated. Always include the textual status.

Report the current consolidation request, confirmed findings and decisions, visible uncertainties, and actual delivery or persistence results. Delivering text is not proof of saving a file. Diagnostic output does not require final confirmation, saving, or a new proposal after the requested result is complete. Any return transition still requires the shared explicit-confirmation protocol.

Present actual questions in the ordinary response using the [shared question format](../SKILL.md#present-questions). In diagnostic `Phase Agent Action Proposal` fields, cite the question identifier and purpose rather than repeating the question or introducing another identifier.

### Readable Layout

- Put each field or section heading in its own paragraph, with a blank blockquote line (`>`) between sections and before and after lists. Do not join multiple fields into one paragraph.
- Under Results, put each check summary in a separate Markdown bullet: `> - 🟩 **Request Clarity — Clear**`. A control-only or no-check explanation is one separate bullet.
- In Extended output, follow Results with a separate bold heading for each evaluated check's criteria. Put every criterion in its own Markdown bullet containing its name, status, and one or two explanatory sentences. Never concatenate criteria in a single paragraph or rely on soft line breaks to separate them.
- Keep Input Interpretation, Agent Actions Taken, and `Phase Agent Action Proposal` as separate labeled sections, with their content in paragraphs below the labels. Keep the comma-separated `Phase Agent Check Set` on its own field line. Preserve the existing field order and level-specific omissions.

## Simplified Level

Include only the heading and these fields, in order:

1. **`Skill Phase`:** `Results Consolidation`.
2. **`Phase Agent Check Set`:** Names of the checks actually selected for the active phase's work in this exchange, separated by commas. Use None for a control-only turn or when no checks were selected for this phase; do not create a catalog merely to populate this field.
3. **Results:** One compact entry per selected check. Preserve an existing outcome name where the applied instruction defines one. If no named outcome is defined, use 🟩 Clear without explanation for a satisfied requirement, 🟨 Clarification Required: with one or two sentences for material ambiguity, or Findings: with one or two sentences for another limitation, conflict, or evidence gap. Use 🟥 for an established conflict or blocker and 🟨 for other unresolved findings. These are diagnostic summaries, not new workflow gates. For a selected check that could not be evaluated, use ⬜ Not Evaluated: with its dependency. For a control-only turn, use ⬜ Not Applicable: Only the diagnostic output setting was handled.

Do not include input interpretation, criterion details, actions, or `Phase Agent Action Proposal` at this level. An unresolved choice accurately represented in a deliberately limited result does not by itself mean the result is blocked.

## Extended Level

Keep the simplified fields and check summaries, adding the following in this order:

1. After `Skill Phase`, add **Input Interpretation:** one paragraph describing the requested synthesis, revision, explanation, saving operation, or return transition and its scope. Distinguish requests about the result from requests to modify the skill itself.
2. After the check summaries, report the result for every criterion used by each selected check, with a status and one or two sentences. Use the actual criteria of the applied shared instruction. Depending on the selected work, these can concern the requested output, preservation of accepted decisions, visible uncertainty, confirmed transitions, or successful saving. Do not add mandatory inputs, classifications, or checks just for this display. Mark inapplicable and unevaluated criteria honestly.
3. Add **Agent Actions Taken:** one or two short paragraphs describing actual synthesis, corrections, delivery, save attempts and verified outcomes, or a pending transition request. Distinguish attempted from successful saving and proposed from confirmed changes.
4. Add **`Phase Agent Action Proposal`:** the next interaction actually presented. If delivery completes the request, the user stops, or only a mode control was handled, state None and the reason. Do not create another confirmation ceremony to populate this field.

For example, if the user requests a summary in chat and the skill delivers it with unresolved choices clearly identified, the actions field reports delivery in chat. It must not claim that a file was saved or that the unresolved choices were accepted. Preserve term names and statuses while writing explanations in the user's language.

## Fixed Input in Diagnostics

Use existing fields to distinguish the validated input baseline from subsequent findings and local choices. Report a request to change that baseline as requiring a new run, not as an accepted revision. Do not claim revalidation merely because the baseline was consulted.

When the input-alignment review finds a departure, describe the affected original condition and actual result in existing findings and Agent Actions Taken. Distinguish a reported departure from a corrected one and chat disclosure from verified saving. Do not invent another `Phase Agent Check` or omit the departure from the ordinary result because diagnostics contain it.
