# Diagnostic Output for `Topic And Context`

Read this reference only while `Debug Mode` is enabled and `Topic And Context` is active. Use the definitions and terminology rules in [the skill's terms](../SKILL.md#terms), the [shared mode controls](../SKILL.md#debug-mode), and the [phase workflow](topic-and-context.md). This reference defines diagnostic presentation, not additional checks or approval requirements.

## Presentation

Follow the [single active-phase block rule](../SKILL.md#output-boundaries). After a confirmed transition, show only the destination phase's diagnostics; never include the outgoing phase's check list or findings. In Extended output, Agent Actions Taken may briefly record the transition. If no checks were selected for the destination phase yet, use None and Not Applicable with that reason rather than borrowing earlier checks.

After a mode control, follow the [shared redisplay rule](../SKILL.md#redisplay-after-controls): acknowledge the setting, repeat the previous ordinary message, handle any additional substantive input, then show the current diagnostic block. The repeat preserves question identifiers and does not rerun earlier checks or reopen decisions. In extended output, report redisplay as a presentation action; cite any still-pending question separately from a new proposal. When the mode is disabled, redisplay still applies but this diagnostic format does not.

Put the ordinary response and any mode-change acknowledgment before one separate Markdown blockquote headed **`Debug Mode` · Simplified** or **`Debug Mode` · Extended**. Use a `>` prefix for every line, including blank lines, so all diagnostic fields remain in the same block. Do not wrap the rendered block in a code fence or use color-dependent HTML.

Use colored markers only for results: 🟩 for clear or ready findings, 🟨 for clarification, missing evidence, or a Not Ready result, 🟥 for an established conflict or blocker, and ⬜ for a criterion that is not applicable or a selected check not evaluated. Always include the textual status; color alone does not convey the result. A Not Ready result is not automatically an established contradiction.

Use the initial or current topic-and-context input. Distinguish proposed framing from confirmed context. For Phase Transition Readiness, report the shared entry requirements for `Exploration And Refinement`.

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

### Check Result Conventions

- **Request Clarity:** Use 🟩 Clear without explanation, or 🟨 Clarification Required: followed by one or two sentences stating the unresolved subject, intention, scope, or relationship and why it matters.
- **Context Consistency And Impact:** Preserve its per-criterion findings. In the simplified display, use 🟩 Clear without explanation only when those findings contain no relevant unresolved issue. Otherwise use Findings: followed by one or two sentences summarizing the conflict, dependency, missing evidence, or uncertain consequence; select 🟥 for an established conflict or blocker and 🟨 otherwise. Clear and Findings are display summaries, not replacement outcomes or permission to discard the underlying findings.
- **Phase Transition Readiness:** Preserve 🟩 Ready without explanation or 🟨 Not Ready: followed by one or two sentences identifying the missing entry information or blocking gap. Do not relabel these as clarity outcomes.
- If a selected check could not be evaluated, use ⬜ Not Evaluated: and briefly state the dependency. Do not imply that all checks passed because only one was completed.

## Extended Level

Keep the simplified fields and check summaries, adding the following in this order:

1. After `Skill Phase`, add **Input Interpretation:** one paragraph describing the user's understood intentions, their subjects and scope, and consequential ambiguity. Mention applicable classification categories and feedback attributes without inventing an intention from each attribute.
2. After the check summaries, add each evaluated check's criterion results, with a status and one or two sentences per criterion. For Request Clarity, cover Intent, Subject, Scope, and Relationships. For Context Consistency And Impact, cover Applicable Baseline, Revision Boundaries, Consistency, Dependencies And Impact, and Evidence For Consequences. For Phase Transition Readiness, cover Required Entry Information, Blocking Gaps, and Available Working Context. Mark genuinely inapplicable criteria Not Applicable and unresolved or unevaluated criteria honestly. Do not force a consistency finding into Clarification Required when it is a conflict or evidence gap.
3. Add **Agent Actions Taken:** one or two short paragraphs reporting actual responses, corrections, questions, retained or changed decisions, and tool actions where relevant. Distinguish a pending proposal from a completed change. Do not report a rejected or unselected action as performed.
4. Add **`Phase Agent Action Proposal`:** the next interaction actually presented to the user and its intended decision or clarification. If none is needed, state None and the completion, stopping, or control-only reason; do not manufacture a proposal for this field.

## Illustrative Output

If the user requests an explanation of "the second term" while two lists remain plausible, a simplified block can be:

> **`Debug Mode` · Simplified**
>
> **`Skill Phase`:** `Topic And Context`
>
> **`Phase Agent Check Set`:** Request Clarity
>
> **Results:**
>
> - 🟨 **Request Clarity — Clarification Required:** Two lists match the reference. The intended term has not been identified.

At the extended level, the same case adds one input-interpretation paragraph, the four Request Clarity criteria, and the final two fields. For example, the actions paragraph can say: "Asked which of the two lists contains the intended term. Topic and context remain unchanged while the list reference is clarified." The proposal cites that question's actual identifier, for example "Q1 — clarify the intended list," rather than asking it again. Use the actual next identifier in the ordinary response; illustrative Q1 labels do not restart numbering. Translate explanatory prose into the user's language while preserving term names and statuses.
