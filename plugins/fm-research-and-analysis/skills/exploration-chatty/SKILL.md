---
name: exploration-chatty
description: Explore a topic through an ongoing dialogue with interim findings, comparisons, and recommendations; incorporate feedback and retain accepted decisions. Use for collaborative investigation and approach refinement, including requested decision records, diagnostic guidance, and implementation instructions. Does not apply changes or require a prior clarification document or research brief.
---

# Exploration Chatty

Help the user develop understanding and a workable approach through substantive discussion. Each iteration should answer the current question, incorporate new evidence or choices, and leave a coherent basis for continuing. The outcome may be an explanation, comparison, decision, or instructions; do not require solution selection when understanding is the goal.

This is a standalone workflow. Do not require other skills, a formal research brief, an initial questionnaire, or a fixed sequence of artifacts. A simple factual question alone does not need this workflow unless it belongs to an ongoing exploration.

## Terms

- `Skill Phase` — A distinct part of the skill's workflow with a specific focus.
- `Phase User Move` — A meaningful user response to a `Phase Agent Action Proposal` within the current `Skill Phase`, including permitted free-form input such as a question, clarification, correction, or alternative proposal.
- `Phase Agent Input Classification` — The agent's classification of the intentions expressed in initial input or a `Phase User Move`, identifying every applicable category and the content each intention concerns.
- `Phase Agent Check` — A check through which the agent evaluates a specific requirement for the current state of work in a `Skill Phase`. Each step has its own set of checks; their results provide the basis for subsequent actions.
- `Phase Agent Check Set` — A set of `Phase Agent Check` evaluations defined for a particular step of a `Skill Phase` and performed by the agent before selecting the next `Phase Agent Action Proposal`. The set may differ between steps.
- `Phase Agent Action Proposal` — The next step in interaction with the user, selected by the agent after completing a `Phase Agent Check Set`. The agent presents it as a question, a confirmation request, or a proposed action whose further execution depends on the user's response. The proposed interaction may explicitly allow confirmation, a question, a clarification, or other free-form input.
- `Topic And Context` — The `Skill Phase` focused on establishing the topic and relevant context.
- `Exploration And Refinement` — The `Skill Phase` focused on investigation, developing understanding, and incorporating user feedback.
- `Results Consolidation` — The `Skill Phase` focused on consolidating the exploration's results.
- `Debug Mode` — An optional diagnostic output mode maintained throughout the current skill workflow. It has simplified and extended detail levels and uses the active `Skill Phase`'s diagnostic instructions to report input interpretation, check results, and agent actions.

### Terminology Use

Distinguish this skill's defined terms from terminology used for the subject of the task or its results.

- When explaining this skill's workflow choices, debugging its behavior, discussing corrections, or preparing materials about improving or modifying the skill itself, use the relevant terms defined in `Terms`. This lets the user refer to the same unambiguous concepts when requesting changes.
- When referring to a defined concept, use its exact term name in inline code delimited by single backticks. Do not treat ordinary vocabulary as a defined term. Preserve required syntax in code, commands, configuration, exact identifiers, and quotations.
- Do not carry this skill's internal terminology into ordinary recommendations, requests for decisions about the subject, research findings, or resulting documents when they are not about the skill itself.
- If the user requests terminology for an investigation, discussion, or resulting document, introduce an independent vocabulary for that subject or result. Such a request does not imply using or inheriting this skill's `Terms`.

Apply this distinction by subject, regardless of delivery format, including chat, saved documents, and corresponding portions of templates. A template's workflow guidance uses this skill's terms; its output content follows the terminology of the intended result.

## Skill Phases

The following references contain `Skill Phase` logic and reserve space for further details and `Phase User Move` guidance. Apply the available instructions alongside the shared workflow below. The [phase-transition requirements](#phase-transitions) apply even where detailed phase guidance remains unfinished. Read only the reference relevant to the `Skill Phase` being discussed or worked on.

### `Topic And Context`

Read [phase guidance](references/topic-and-context.md) when establishing the topic and relevant context for `Topic And Context`, including at the start of a new exploration.

### `Exploration And Refinement`

Read [phase guidance](references/exploration-and-refinement.md) when working on `Exploration And Refinement`.

### `Results Consolidation`

Read [phase guidance](references/results-consolidation.md) when working on `Results Consolidation`.

## `Debug Mode`

### Controls and State

Keep `Debug Mode` in conversation context as Off, Simplified, or Extended. Default to Off for a new exploration. Preserve the setting throughout the current skill workflow, including forward and return phase transitions and resumption when the setting is available in context. Do not infer a previously enabled setting when that context is unavailable. No tracking file is required.

Accept all of the following forms, including clear equivalents in the user's language and ordinary capitalization variations. These are instructions in chat, not commands that require host integration.

| Form | Simplified | Extended | Off |
|---|---|---|---|
| Ordinary language | "Enable simplified debug." | "Enable extended debug." | "Turn debug off." |
| Explicit setting | `Debug Mode: Simplified` | `Debug Mode: Extended` | `Debug Mode: Off` |
| Compact marker | `[debug:simplified]` | `[debug:extended]` | `[debug:off]` |

Apply an unambiguous control request before processing the rest of that turn; the resulting setting applies to the current response. A clear request to enable debugging without specifying a level selects Simplified. If the intended setting remains ambiguous, retain the existing setting and ask one focused question. Quoted examples or discussion of how to use a control do not change the setting unless the user requests its application.

Explicitly acknowledge every enable, disable, or level change outside the diagnostic block, in the user's language. State the resulting setting, for example, "`Debug Mode` enabled: Simplified," "`Debug Mode` changed to Extended," or "`Debug Mode` disabled." If the requested setting is already active, say that it is already active rather than claiming a change. When disabled, acknowledge the action but omit diagnostic output from that response onward.

Treat these controls as output settings before phase-specific input classification. A clear control request does not by itself add a substantive intention or trigger mixed-input action selection. Process the remaining input under the existing workflow; enabling debugging is not confirmation of a decision, revision, or phase transition. A control-only turn needs no manufactured research checks, follow-up proposal, or extra confirmation.

### Redisplay After Controls

After acknowledging an enable, disable, or level-change request, redisplay the complete ordinary message most recently sent to the user before that control request. Apply this also when acknowledging that the requested setting is already active. Preserve its wording, Markdown, question identifiers, choices, and reply examples; do not replace it with a summary or a statement that a question remains open. Exclude prior diagnostic blocks and mode-control acknowledgments from the redisplayed content. For consecutive control-only turns, reuse the same last ordinary message rather than nesting earlier control responses. If that message is unavailable in context, state that it cannot be redisplayed faithfully; do not reconstruct it from guesses.

Use this response order: setting acknowledgment, redisplayed ordinary message, response to any additional substantive input in the same turn, then diagnostic output at the resulting level when enabled. Clearly label the redisplayed message in the user's language. If the turn also answers an old question or changes the work, identify the repeat as the previous message and distinguish the new response and current question status from that historical content. When disabling the mode, still redisplay the message but omit diagnostic output.

Redisplay is a presentation operation, not renewed investigation, a new `Phase Agent Action Proposal`, confirmation, or a phase transition. Do not rerun checks, repeat tool actions, reopen resolved questions, or allocate new question identifiers merely to repeat the message. On a control-only turn, report only the setting change and redisplay as current actions; do not present the repeated message's earlier checks or actions as newly performed. A still-pending proposal remains pending with its existing identifier. Ordinary later replies follow the normal workflow without automatic redisplay.

### Conditional Reference Loading

Read only the diagnostic reference for the active `Skill Phase`, and only while `Debug Mode` is enabled:

| Active phase | Diagnostic reference |
|---|---|
| `Topic And Context` | [Diagnostic output](references/topic-and-context-debug.md) |
| `Exploration And Refinement` | [Diagnostic output](references/exploration-and-refinement-debug.md) |
| `Results Consolidation` | [Diagnostic output](references/results-consolidation-debug.md) |

On enabling the mode partway through a phase, read that phase's diagnostic reference before producing the block. On a confirmed phase transition with the mode enabled, retain its level and read the destination's diagnostic reference when entering that phase. Do not preload references for inactive phases or read diagnostic references while the mode is Off. Reuse a reference already available in context; reread it only if needed to recover unavailable or changed instructions.

### Output Boundaries

When enabled, follow the active phase's diagnostic format after the ordinary response, in a separate Markdown blockquote. Use exact defined terms for diagnostic labels, text statuses alongside colored result markers, and explanations in the user's language. Keep internal terminology out of ordinary subject-matter recommendations and deliverables under the terminology rules above.

Report concise interpretations, applied criteria, check findings, and observable actions. Do not present a private reasoning transcript or claim checks, tool use, actions, or outcomes that did not occur. Keep proposed actions distinct from completed actions. The mode does not introduce additional workflow gates or checks, and does not require another proposal after completion or stopping. Save diagnostic output only when requested.

Produce exactly one diagnostic block for the `Skill Phase` active when the response is delivered. After a confirmed transition, use only the destination phase's format while preserving the selected level; do not output a second block, check list, results, or criterion details for the outgoing phase. A proposed or unconfirmed transition leaves the current phase active. In Extended output, the Agent Actions Taken field may briefly note the completed transition without reproducing its earlier check results.

List only checks selected for the active phase's work and report their actual findings. Do not relabel outgoing-phase checks as destination-phase checks or rerun checks merely to populate the block. If no checks were selected for the destination phase yet, use None for `Phase Agent Check Set` and Not Applicable with that reason for Results. Preserve honest Not Evaluated findings for any selected checks that have not been evaluated.

## Phase Transitions

Start a new exploration in `Topic And Context`. On resumption, retain the last confirmed `Skill Phase` when the available context identifies it. Keep the current phase in conversation context; a saved tracking document is not required.

The forward order is `Topic And Context` → `Exploration And Refinement` → `Results Consolidation`. Do not silently advance or skip phases. Use the return transitions below when earlier work needs to be revisited.

### Readiness Requirements

Assess the following requirements with the applicable `Phase Agent Check` evaluations before proposing a transition:

| Transition | Requirements |
|---|---|
| `Topic And Context` → `Exploration And Refinement` | The topic, intended result, and material scope and constraints are established and confirmed. Enough context is available to identify a useful first investigation step without guessing the user's intentions. Unknown facts that the investigation is meant to establish are not blockers. |
| `Exploration And Refinement` → `Results Consolidation` | The requested final synthesis is understood, and enough findings, reasoning, and current decisions are available to produce it. Unresolved choices and evidence limitations are identified and can be represented accurately in the result. A deliberately limited result may remain incomplete; do not invent agreement or research merely to make it appear final. |
| `Results Consolidation` → `Exploration And Refinement` | Further investigation or substantive analysis is needed beyond editing the current synthesis. Identify the question to reopen, its reason, and the affected findings or decisions. |
| `Exploration And Refinement` or `Results Consolidation` → `Topic And Context` | The topic, goal, scope, or essential context needs renewed clarification or reframing. Identify what must be revisited and why; agreement on the revised framing is obtained within `Topic And Context`, not assumed before returning. |

### Transition Protocol

1. **Assess readiness.** Apply the current phase's admission rules and relevant checks. Keep the current `Skill Phase` unchanged when blocking gaps or unresolved conditions prevent the transition; identify the specific gaps rather than claiming readiness.
2. **Present the transition.** When ready, briefly state what has been established in the current phase, identify the destination and its purpose, and formulate a `Phase Agent Action Proposal` asking for explicit confirmation of that transition. A request to move on does not replace confirmation of a presented transition unless it clearly answers that pending proposal.
3. **Wait for confirmation.** Do not perform destination-phase work before the user explicitly confirms. An unambiguous answer in ordinary language is sufficient when it refers to the pending transition. Confirmation of the topic or a substantive choice alone is not confirmation of a phase transition.
4. **Handle qualifications.** If the reply adds a correction, condition, question, or another independent request, do not treat it as unqualified transition confirmation. Apply the current phase's classification and admission rules, resolve the relevant issues, reassess affected readiness findings, and present the transition again when appropriate. Do not carry a withdrawn or unselected transition forward as an automatic task.
5. **Enter the destination.** After valid confirmation, record the new current phase in conversation context, tell the user that the transition is taking place, and apply the destination reference. Preserve unaffected agreements and visible uncertainties. Do not ask for confirmation of the same unchanged transition again.

Apply this protocol to both forward and return transitions. Refinement within the current phase is not itself a phase transition, though its content may require confirmation under that phase's rules. Interim findings, explanations, and progress summaries do not automatically start `Results Consolidation`.

The user may stop in any phase. Stopping or completing the immediate request does not require entering `Results Consolidation`, confirming another transition, or saving an artifact. Within `Results Consolidation`, deliver the requested result under the completion and saving rules below; no additional phase or final confirmation ceremony is required.

## Interaction Cycle

Apply any [diagnostic output controls](#controls-and-state) first, then use the remaining input for this cycle. Apply the current `Skill Phase`'s input-admission and confirmation requirements before executing requested actions, adopting revisions, or recording acceptance. Clear meaning alone does not override a phase-specific requirement for separate selection or confirmation.

1. **Identify the input.** At invocation, use the available initial input and relevant context; no preceding `Phase Agent Action Proposal` is required. During the ongoing dialogue, use the received `Phase User Move` and current working context.
2. **Classify intentions.** Perform `Phase Agent Input Classification`. Identify all expressed intentions and the content each concerns, including confirmations, corrections, and explanatory questions. These categories are not exhaustive. A free-form response may contain several intentions at once; do not force the whole message into one category. Classification identifies what needs processing; it does not establish clarity, completeness, or consistency, or apply requested changes.
3. **Select the checks.** Use the classification and current step to select the applicable `Phase Agent Check Set`, covering intentions relevant to that step and their dependencies on other parts of the input. Use phase-specific instructions where defined; until detailed sets are specified, select checks from the requirements already stated for the current work in this skill and its relevant references. A narrow explanatory question may use a short set; do not skip the set or repeat unrelated checks merely to fill it out.
4. **Evaluate the current state.** Perform the selected `Phase Agent Check Set`, considering the full response, proposed changes, current evidence, and affected earlier decisions. Completing the set means obtaining its results, not satisfying every checked requirement. Unclear or conflicting content may require clarification; missing evidence may require inspection or a visible limitation. A clear revision can replace an earlier choice after any required phase-specific confirmation; assess its consequences without treating the earlier confirmation as a prohibition on change.
5. **Respond and propose the next interaction.** Use the results to answer the request and, when continuing the dialogue, select and present the next `Phase Agent Action Proposal`. When comparing alternatives, apply the [return-to-comparison guidance](#return-to-the-overall-comparison) before choosing the continuation. Present any question using the [shared question format](#present-questions). A question or clarification submitted through an offered free-form response is an explicitly permitted continuation. An explanatory question can expose a material error or contradiction: if it does, perform the affected checks before forming the next proposal, and correct established agent errors without requesting unnecessary clarification. Do not treat the question alone as acceptance or a request to revise unrelated decisions.
6. **Repeat after the response.** Incorporate all understood parts of the next `Phase User Move` into the next pass through classification and checks. Account for confirmations, corrections, and questions expressed in the same user response while following any phase-specific processing order, without prescribing a count of moves per message. Apply the completion and stopping rules below; do not manufacture another proposal when the request is complete or the user stops.

## Present Questions

Use this format for every question actually addressed to the user in every `Skill Phase`, including clarification, action selection, decision confirmation, phase-transition confirmation, missing information, and ambiguous mode controls. Apply it to the question within a `Phase Agent Action Proposal`; it does not turn every answer or proposal into a question. Internal check criteria, quoted user questions, research questions in deliverables, and diagnostic references to an already presented question are not new questions addressed to the user.

### Layout and Identifiers

- Start each question with `❓ **Q1 — Short title:** Question text`, substituting its actual identifier, a concise topic label, and a concrete question. Localize the title, wording, choices, and reply instruction to the user's language. Render ordinary Markdown rather than enclosing actual questions in code fences or relying on fixed text colors.
- Use Q1, Q2, and subsequent numbers as stable identifiers throughout the current exploration, including phase transitions. Keep the identifier when clarifying the same question; assign the next unused number to a new question or substantively different proposal. Do not silently reuse a number for another decision or change what an existing answer letter means. Numbering stays in conversation context and does not require a file. Illustrative identifiers in references do not restart the actual numbering.
- Where meaningful alternatives exist, list them as bullets labeled **A.**, **B.**, and subsequent letters. Include a final **Custom answer** choice inviting a correction, question, or alternative. Use as many substantive choices as needed; do not pad the list to a fixed count or combine unrelated decisions into one choice. State the exact subject, boundaries, and consequences needed for a meaningful selection.
- Follow the choices with a reply example using the actual identifier and letters, such as `Q1: A` or `Q1: C — <your answer>`. If there are no useful preset alternatives, use a **Custom answer:** prompt and an example such as `Q2: <your answer>` without artificial A/B choices.
- Put necessary findings, proposed wording, scope boundaries, and workflow restrictions before the question. The layout does not replace phase-specific readiness, action-selection, or confirmation requirements. Do not present a transition-confirmation question until readiness permits it.

Illustrative choice layout; use the actual next identifier and localize the content:

❓ **Q1 — Scope of exclusion:** Exclude `YYYYMMDD-topic` as a standalone scheme or keep it for comparison with its deficiency recorded?

- **A.** Exclude only the standalone scheme `YYYYMMDD-topic`.
- **B.** Keep it for comparison with the deficiency recorded.
- **C. Custom answer** — Clarify another action, ask a question, or correct the scope.

Reply, for example: `Q1: A` or `Q1: C — <your answer>`.

Illustrative free-response layout:

❓ **Q2 — Identifier scope:** Across which collection must identifiers remain unique?

**Custom answer:** Describe the collection and its boundaries.

Reply, for example: `Q2: across all research documents in my projects`.

### Answers and Workflow

Accept clear ordinary prose as well as identifier-and-letter answers. A bare letter is sufficient when one pending question makes its meaning unambiguous. If several questions are pending, accept any clear mapping and ask only about unresolved references. Do not reject a meaningful free-form answer, question, correction, or stop request because it lacks the suggested syntax.

Interpret the complete response, including qualifications; a selected letter does not override contradictory or conditional text. A clear, unqualified selection of an already presented confirmation option can satisfy explicit confirmation for that exact proposal. Do not ask again merely because the answer is a letter, and do not treat a subject-matter choice as phase-transition consent. Classify and check qualified or compound answers under the current phase's existing rules.

The common layout does not set a fixed number of questions per response or schedule future actions. Keep dependent decisions separate where the workflow requires it. If several questions are appropriate together, give each its own identifier and choices, and include a reply example mapping each answer to its question. Do not repeat resolved questions or manufacture a question when the current request is complete or the user stops. The labeled [redisplay after mode controls](#redisplay-after-controls) preserves prior questions as historical content without reopening them.

When `Debug Mode` is enabled, keep the actual question in the ordinary response before the diagnostic block. In diagnostic `Phase Agent Action Proposal` fields, reference its identifier and purpose rather than repeating it as another question or assigning it another identifier.

## Start from Available Context

Provide a useful initial analysis at the requested level of detail. Do not make the user supply findings that the exploration is meant to establish.

Use available research and read capabilities within the authorized scope. Inspect relevant evidence rather than asking the user to repeat accessible facts. Verify version-dependent or uncertain claims with appropriate sources when available, linking material findings to their sources. Distinguish observed facts, user-reported information, assumptions, and recommendations. Do not invent prior context, access, verification, or results.

No particular tool, service, or credential is required. Research, inspection, and saving depend on host capabilities. When a capability or source is unavailable, explain which conclusion remains uncertain and continue with supported analysis; request targeted evidence if it is necessary. A recommendation may remain provisional while useful discussion continues.

## Run an Adaptive Discussion

Use the [interaction cycle](#interaction-cycle) for each exchange; apply the following discussion guidance within that cycle.

1. **Answer and recommend.** Address the user's immediate question using the current constraints and evidence. Where alternatives matter, explain their consequential advantages and drawbacks and recommend an approach with reasons. Avoid padding comparisons with implausible alternatives.
2. **Make the proposal discussable.** Group related decisions and give them descriptive titles; use stable numbering when it helps the user refer to several proposals. Discuss complex or dependent questions separately when useful. Match depth to the request instead of enforcing one decision per turn or a complete design in every reply.
3. **Incorporate the response.** Interpret ordinary prose and selections by title or number. Apply the current `Skill Phase`'s admission and confirmation requirements. Where those requirements are satisfied, an unambiguous choice accepts the relevant proposal without another confirmation ceremony. Apply qualifications and partial acceptance precisely; unaddressed proposals remain undecided but are not automatically scheduled for later work. Acknowledging an explanation does not necessarily accept an unrelated recommendation.
4. **Check the consequences.** Compare new information and choices with the working approach and its dependencies. Explain what changes and why. Preserve unrelated agreements. If the approach still fits, say so briefly when useful and proceed without inventing a revision.
5. **Continue at the useful boundary.** Summarize material changes or the current conclusion, applying the [return-to-comparison guidance](#return-to-the-overall-comparison) when alternatives are being compared, then pursue the requested next step or offer a relevant continuation. Ask when a consequential user choice is needed. Do not manufacture questions, optional research, or repeated checkpoints to prolong the conversation.

Use plain working language in the user's language. Explain technical terms when needed; retain precise identifiers. Use diagrams, tables, examples, or numbered sections when they improve understanding. The length and layout of the source conversation are not a fixed response template.

## Preserve Decisions While Allowing Revision

Maintain the current goal, constraints, accepted decisions and their reasons, proposed alternatives, relevant evidence, and unresolved questions in conversation context. Surface the parts needed to understand the current response; do not repeat a full ledger every turn or create a working file automatically.

- Clear user revisions identify the specified earlier choices to replace. Where the current `Skill Phase` requires confirmation, retain the revision as proposed until confirmed. After acceptance, update the affected choices and explain material downstream effects without reopening unaffected decisions.
- When new evidence undermines an accepted approach, identify the affected assumption, explain the implication, and recommend a revision. Do not present that recommendation as a user decision already made.
- When the user's intended change or its interaction with another requirement is ambiguous, ask a focused question instead of silently choosing which requirement to discard. Continue independent analysis where possible.
- An explanation-only request is answered against the current approach. Change it only if the explanation exposes a real error or the user also requests a change.
- Silence, omitted answers, and requests for a summary do not accept unresolved proposals. Label consequential defaults as proposals or assumptions rather than incorporating them as agreed values.
- On resumption, use available conversation context or a supplied summary. If essential context is missing, request only the missing portion; do not reconstruct agreements from guesses.

Distinguish decisions about what should be done from evidence of what has actually been done. Preparing a document or receiving general agreement does not establish successful implementation.

## Return to the Overall Comparison

When an exploration compares alternatives, keep the overall comparison visible while working through a narrower question: overall comparison → current focus → specific question → substantive result → overall perspective → justified next step. This happens within the current `Skill Phase`; it is neither a phase transition nor a new confirmation requirement. Existing classification, input-admission, confirmation, completion, and stopping rules continue to apply.

### Candidate State and Decision Boundaries

For each significant candidate, retain in conversation context what is being considered; whether it remains included, is explicitly excluded, or is explicitly deferred; material findings and limitations; accepted decisions with their exact boundaries; and unresolved questions that materially affect comparison. Preserve reasons for exclusion for relevant results. No tracking file, permanent response table, or formal scoring system is required.

Distinguish the current discussion focus, selection of a parameter or configuration for one candidate, selection of that candidate as the overall approach, and exclusion of other candidates. A focus change, favorable evaluation, or local decision alone changes none of the other candidates' statuses. Record an explicit exclusion or deferral only under the existing admission and confirmation rules. Keep excluded candidates outside the active comparison unless there is a stated basis for reconsideration; do not silently reinstate them.

Candidate state is research context, not an execution queue. An open candidate does not become an automatically scheduled task, and retaining it does not revive an unselected user request. Do not use the overview to prompt a return to an unselected request merely because its candidate remains open. Follow the phase's existing selection rules before processing such a request.

### When and How to Return

Bring the comparison back into view after answering a substantive question in the focused analysis, accepting a significant local choice, or discovering a limitation that changes the comparison. Also do so before another step would risk extending one candidate's analysis while leaving the others invisible. Combine several triggers in one response into one concise overview.

Answer a direct question first. Add the overview where it helps determine continuation; do not substitute it for the answer. A short explanation, diagnostic setting acknowledgment or redisplay, or progress message without a substantive result does not itself trigger an overview. Stop when asked, without an added overview or procedural question. For a requested limited result, respect its scope and mark consequential limits; do not expand it into a full comparison or require further investigation for completeness.

Briefly state what the focused analysis established, the exact boundaries of any accepted decision, which other significant candidates remain open, which gaps prevent a sound comparison, and the recommended next step with its reason. If no local choice was accepted, do not invent one. Do not repeat the full research history. Group related candidates only when this preserves material differences in their status.

### Choose a Justified Continuation

Base the next step on the investigation's goal, available evidence, comparison gaps, and the user's interest. Continuing the same candidate is allowed; explain why it is currently more useful than examining another open candidate. Unequal investigation depth is not evidence of superiority. Equal depth is not required: an early recommendation may be useful if its provisional nature and material gaps are explicit.

Honor an explicit request to focus on one candidate. Keep other candidates open unless the user changes their status, without imposing their detailed investigation or repeatedly restating the full comparison. The overview does not require a user selection; ask only when the next step genuinely depends on a user decision under the existing workflow. Preserve completion, stopping, and confirmed phase-transition boundaries rather than adding a continuation ceremony.

## Produce Requested Materials

Read [deliverables](references/deliverables.md) when the user requests a summary, decision record, diagnostic collection, or implementation instructions. These are optional continuations, not mandatory stages. Adapt other requested document types to their intended use.

Keep accepted decisions and their rationale coherent across artifacts. New evidence may justify an updated recommendation; identify it explicitly rather than quietly rewriting the accepted baseline. An artifact must stand on its own without requiring the reader to reconstruct the chat. Preserve unresolved questions and unverified prerequisites where they matter.

This workflow may research, inspect, prepare documents and diagnostic commands, and analyze user-supplied results. It does not apply configuration changes, deploy, or execute an implementation runbook. If asked to perform implementation, explain the boundary and hand off the current decisions, prerequisites, and requested actions to a separate implementation task; do not mistake that request for permission to execute within this workflow.

## Finish or Save

The current request is complete when its question is answered or requested material is delivered, with material uncertainty visible and accepted decisions preserved. File persistence is not a prerequisite for completing a discussion. Stop when the user stops; do not force a final confirmation or artifact.

Create or update a saved artifact only when requested. Use the user's destination or an applicable host saving convention; ask for a destination only when needed. Honor existing authorization to update a document and preserve unrelated content. If saving fails or is unavailable, provide the content in chat and state that persistence remains incomplete. Claim a saved location only after successful writing.
