---
name: exploration-chatty
description: Explore a topic through an ongoing dialogue with interim findings, comparisons, and recommendations; incorporate feedback and retain accepted decisions. Use for collaborative investigation and approach refinement, including requested decision records, diagnostic guidance, and implementation instructions. Does not apply changes or require a prior clarification document or research brief.
---

# Exploration Chatty

Help the user develop understanding and a workable approach through substantive discussion. Each iteration should answer the current question, incorporate new evidence or choices, and leave a coherent basis for continuing. The outcome may be an explanation, comparison, decision, or instructions; do not require solution selection when understanding is the goal.

This is a standalone workflow. Do not require other skills, a formal research brief, an initial questionnaire, or a fixed sequence of artifacts. A simple factual question alone does not need this workflow unless it belongs to an ongoing exploration.

## Start from Available Context

Use the topic, supplied materials, and relevant conversation context. If no topic can be identified, ask for it. Otherwise provide a useful initial analysis at the requested level of detail; ask only about missing information that materially affects the answer or next step. Do not make the user supply findings that the exploration is meant to establish.

Use available research and read capabilities within the authorized scope. Inspect relevant evidence rather than asking the user to repeat accessible facts. Verify version-dependent or uncertain claims with appropriate sources when available, linking material findings to their sources. Distinguish observed facts, user-reported information, assumptions, and recommendations. Do not invent prior context, access, verification, or results.

No particular tool, service, or credential is required. Research, inspection, and saving depend on host capabilities. When a capability or source is unavailable, explain which conclusion remains uncertain and continue with supported analysis; request targeted evidence if it is necessary. A recommendation may remain provisional while useful discussion continues.

## Run an Adaptive Discussion

1. **Answer and recommend.** Address the user's immediate question using the current constraints and evidence. Where alternatives matter, explain their consequential advantages and drawbacks and recommend an approach with reasons. Avoid padding comparisons with implausible alternatives.
2. **Make the proposal discussable.** Group related decisions and give them descriptive titles; use stable numbering when it helps the user refer to several proposals. Discuss complex or dependent questions separately when useful. Match depth to the request instead of enforcing one decision per turn or a complete design in every reply.
3. **Incorporate the response.** Interpret ordinary prose and selections by title or number. An unambiguous choice accepts the relevant proposal without a second confirmation ceremony. Apply qualifications and partial acceptance precisely; unaddressed proposals remain open. Acknowledging an explanation does not necessarily accept an unrelated recommendation.
4. **Check the consequences.** Compare new information and choices with the working approach and its dependencies. Explain what changes and why. Preserve unrelated agreements. If the approach still fits, say so briefly when useful and proceed without inventing a revision.
5. **Continue at the useful boundary.** Summarize material changes or the current conclusion, then pursue the requested next step or offer a relevant continuation. Ask when a consequential user choice is needed. Do not manufacture questions, optional research, or repeated checkpoints to prolong the conversation.

Use plain working language in the user's language. Explain technical terms when needed; retain precise identifiers. Use diagrams, tables, examples, or numbered sections when they improve understanding. The length and layout of the source conversation are not a fixed response template.

## Preserve Decisions While Allowing Revision

Maintain the current goal, constraints, accepted decisions and their reasons, proposed alternatives, relevant evidence, and unresolved questions in conversation context. Surface the parts needed to understand the current response; do not repeat a full ledger every turn or create a working file automatically.

- Clear user revisions replace the specified earlier choices. Explain material downstream effects without reopening unaffected decisions.
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
