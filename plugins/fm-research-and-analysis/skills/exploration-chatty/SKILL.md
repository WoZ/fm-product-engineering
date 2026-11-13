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

Apply the current `Skill Phase`'s input-admission and confirmation requirements before executing requested actions, adopting revisions, or recording acceptance. Clear meaning alone does not override a phase-specific requirement for separate selection or confirmation.

1. **Identify the input.** At invocation, use the available initial input and relevant context; no preceding `Phase Agent Action Proposal` is required. During the ongoing dialogue, use the received `Phase User Move` and current working context.
2. **Classify intentions.** Perform `Phase Agent Input Classification`. Identify all expressed intentions and the content each concerns, including confirmations, corrections, and explanatory questions. These categories are not exhaustive. A free-form response may contain several intentions at once; do not force the whole message into one category. Classification identifies what needs processing; it does not establish clarity, completeness, or consistency, or apply requested changes.
3. **Select the checks.** Use the classification and current step to select the applicable `Phase Agent Check Set`, covering intentions relevant to that step and their dependencies on other parts of the input. Use phase-specific instructions where defined; until detailed sets are specified, select checks from the requirements already stated for the current work in this skill and its relevant references. A narrow explanatory question may use a short set; do not skip the set or repeat unrelated checks merely to fill it out.
4. **Evaluate the current state.** Perform the selected `Phase Agent Check Set`, considering the full response, proposed changes, current evidence, and affected earlier decisions. Completing the set means obtaining its results, not satisfying every checked requirement. Unclear or conflicting content may require clarification; missing evidence may require inspection or a visible limitation. A clear revision can replace an earlier choice after any required phase-specific confirmation; assess its consequences without treating the earlier confirmation as a prohibition on change.
5. **Respond and propose the next interaction.** Use the results to answer the request and, when continuing the dialogue, select and present the next `Phase Agent Action Proposal`. A question or clarification submitted through an offered free-form response is an explicitly permitted continuation. An explanatory question can expose a material error or contradiction: if it does, perform the affected checks before forming the next proposal, and correct established agent errors without requesting unnecessary clarification. Do not treat the question alone as acceptance or a request to revise unrelated decisions.
6. **Repeat after the response.** Incorporate all understood parts of the next `Phase User Move` into the next pass through classification and checks. Account for confirmations, corrections, and questions expressed in the same user response while following any phase-specific processing order, without prescribing a count of moves per message. Apply the completion and stopping rules below; do not manufacture another proposal when the request is complete or the user stops.

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
5. **Continue at the useful boundary.** Summarize material changes or the current conclusion, then pursue the requested next step or offer a relevant continuation. Ask when a consequential user choice is needed. Do not manufacture questions, optional research, or repeated checkpoints to prolong the conversation.

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

## Produce Requested Materials

Read [deliverables](references/deliverables.md) when the user requests a summary, decision record, diagnostic collection, or implementation instructions. These are optional continuations, not mandatory stages. Adapt other requested document types to their intended use.

Keep accepted decisions and their rationale coherent across artifacts. New evidence may justify an updated recommendation; identify it explicitly rather than quietly rewriting the accepted baseline. An artifact must stand on its own without requiring the reader to reconstruct the chat. Preserve unresolved questions and unverified prerequisites where they matter.

This workflow may research, inspect, prepare documents and diagnostic commands, and analyze user-supplied results. It does not apply configuration changes, deploy, or execute an implementation runbook. If asked to perform implementation, explain the boundary and hand off the current decisions, prerequisites, and requested actions to a separate implementation task; do not mistake that request for permission to execute within this workflow.

## Finish or Save

The current request is complete when its question is answered or requested material is delivered, with material uncertainty visible and accepted decisions preserved. File persistence is not a prerequisite for completing a discussion. Stop when the user stops; do not force a final confirmation or artifact.

Create or update a saved artifact only when requested. Use the user's destination or an applicable host saving convention; ask for a destination only when needed. Honor existing authorization to update a document and preserve unrelated content. If saving fails or is unavailable, provide the content in chat and state that persistence remains incomplete. Claim a saved location only after successful writing.
