# Brief Dialogue Protocol

Read before any question. [SKILL.md](../SKILL.md) owns mode permission, readiness, direction review transitions, confirmation, and saving; this reference governs presentation and answer handling.

Apply [the brief writing style](../SKILL.md#writing-style) when presenting or discussing any part of the brief, including content outside direction review.

## Present Questions

- Ask in Markdown chat and receive answers as chat messages. Localize the wording to the conversation language.
- Start each question with `❓ **Q1 — Topic:** Question text`, assigning stable identifiers and short topic labels.
- Group related clarification questions in one message, with clear spacing between blocks. Direction review instead presents one direction at a time. Present options as bullets with literal letter identifiers: `- **A.** Choice text`.
- End every choice list with a separate custom-answer option using the next unused letter and an explicit instruction to enter an answer. With no useful predefined options, show only `A. Custom answer — enter your own response.`
- Explain implications briefly when useful. Request separate answers by identifier and give an example such as `Q1: A` and `Q2: C — <your explanation>`.
- Preserve identifiers and option meanings on retries. Assign a new identifier when a question changes materially.

For example, present the mandatory mode choice as follows, localized as needed:

```markdown
❓ **Q1 — Project context:** Should existing project documents and source code be used when preparing the brief?

- **A.** Yes — inspect relevant materials to clarify context, decomposition, and research boundaries.
- **B.** No — Greenfield Zone: prepare the brief from the saved input and clarification dialogue without inspecting existing project documents or code.
- **C.** Custom answer — enter your own response.

Reply by question identifier, for example: Q1: A or Q1: C — <your explanation>.
```

## Review Research Directions

Present only the current direction for review, in the dependency order established by [SKILL.md](../SKILL.md#check-consistency-and-order-directions). Show its current full content and distinguish a blocker-free version awaiting confirmation from a working version requiring clarification:

- Put the stable research label only on the first line beside the title; use titles when referring to directions elsewhere.
- State the research question, then explain the subject, boundaries, plausible investigation paths, and relevance to the user's conclusion or decision in one or two paragraphs.
- Add the research-steps subsection specified in [SKILL.md](../SKILL.md#explain-and-confirm-directions-one-at-a-time): ten numbered, concrete points showing what will be checked and analyzed, tailored to the current direction and its agreed methods. Localize its heading as specified there. Keep the steps in ordinary working language and distinguish them from expected findings.
- Add a separate heading localized as **What the research should produce**, with one or two paragraphs describing the concrete expected information. Use bullets where they make an enumeration clearer. Describe this direction's output rather than its purpose, work steps, or the final result of the whole brief.
- Add a short example. Label hypothetical examples and do not present possible findings as established facts.

Use the same format for user-supplied and agent-proposed directions. A research question describes future work; it is not a demand that the user answer it now. After the complete direction, choose the next question by its current status: ask only necessary clarification questions for a working version with material blockers, or request confirmation when no blockers remain. The following confirmation example applies only to a blocker-free version:

```markdown
❓ **Q4 — Current direction:** Does this description reflect what you want to investigate?

- **A.** Confirm the current description.
- **B.** Revise this direction — describe your changes or ask for more explanation.
- **C.** Custom answer — enter your own response.

Reply by question identifier, for example: Q4: A or Q4: B — limit the comparison to the stated operating conditions.
```

Derive the actual question identifier from the conversation. Interpret answers semantically, preserving qualifications. Allow changes to the wider set of directions as well, including addition, removal, merging, or splitting. For revisions retaining the current direction, apply the understood edits and check dependencies, then show the complete revised direction in the same response under its existing label and title. Include all components listed above, even if some are unchanged; a change summary alone is insufficient. Place explicit notes at ambiguous or conflicting passages, retaining the difference between an accepted condition and an unresolved requested change. Label a blocked direction as a working version and ask only necessary questions after the full display, without a confirmation option. Explicit removal follows the existing deletion rule instead of requesting approval of the removed content.

When an earlier answer conflicts with the revision, explain after the full display which answers are affected and that you will ask those questions again. Reopen only the conflicting questions in dependency order, reusing their wording, choices, and identifiers when unchanged. A materially changed question gets a new identifier. If the earlier wording is unavailable, ask about the recorded condition without claiming to reproduce the original question. Preserve unrelated answers. Follow [the revision and return workflow](../SKILL.md#explain-and-confirm-directions-one-at-a-time); never infer a new accepted answer or resolve competing conditions yourself.

After clarification answers, show the complete updated direction again and ask for confirmation only if material blockers are gone. An edit request or clarification answer itself does not confirm the revised direction. For an explanation-only request, explain the term or provision without mandatory redisplay when content is unchanged. Do not advance to the next direction without confirmation, except when the user explicitly removes the current direction. An omitted, ambiguous, or deferred answer leaves review pending under the answer-handling rules below.

If a change affects earlier confirmations, return to the affected directions for renewed confirmation before dependent review continues. First perform the required full redisplay of the current direction in the revision response; earlier-direction review does not replace it. Keep unaffected confirmations. Once each current direction is confirmed, continue to the finishing choice and full-brief confirmation without a separate collective approval of the list.

## Handle Answers

- Accept a clear letter, custom response, or qualified choice. Preserve qualifications; a response allowing documents only does not allow code inspection.
- Retain accepted answers unless the user revises them. For ordinary clarification, explain ambiguous mapping or an unanswered, contradictory, or off-topic response and re-ask only the unresolved question. During direction revisions, first show the full working version as described above, then ask only the necessary unresolved or reopened questions. An empty custom answer supplies no answer; a conflict makes the affected decision pending clarification rather than silently replacing its accepted answer.
- Treat requests for explanation, corrections, stopping, or changes of direction as dialogue control. Incorporate corrections and reassess affected decisions.
- For “I don't know,” clarify whether explanation, explicit deferral, or assignment to research is intended when the next action is unclear. Do not infer any of these from silence or uncertainty.
- Honor explicit deferrals without repeated retries. Record material effects, but do not convert a skipped decision into a default or research permission. Deferring project-context selection leaves the mode unselected and discovery unavailable.
- Keep confirmation separate from choosing to finish. Ask whether the presented complete brief is accurate and accepted; after material changes, confirm the updated document.

Before sending any question, check its identifier, option letters, final custom-answer option, and reply example.
