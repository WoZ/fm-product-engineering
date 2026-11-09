---
name: exploration-input-clarification
description: Clarify a user's exploration request and save confirmed input for research brief creation. Use for requests to learn, explain, describe, understand, or inform a decision in any subject. Excludes brief creation, research execution, and requests solely to carry out an already defined task.
---

# Exploration Input Clarification

Establish shared understanding through user-controlled clarification rounds, then save confirmed input for brief creation. Exploration can concern any subject, including the behavior, risks, or use of an already selected solution; comparing solutions is not required.

This stage must not create a brief, fully specify or plan research, or conduct research. Brief creation has its own analysis, clarification, and validation.

Throughout the workflow, incorporate user corrections and preserve stated decisions, restrictions, and the force of each condition. Preferences remain preferences, hypotheses remain unverified, and proposed interpretations remain unconfirmed until accepted. Do not replace the problem, impose approaches or technologies, expand scope, or choose between conflicts unless supplied context resolves them.

**Before asking the first question of any kind**, read [the clarification dialogue protocol](references/clarification-dialogue.md). It applies to missing-input requests, clarification, checkpoints, confirmation, and saving-destination questions.

## 1. Read the Supplied Input

Read input supplied in chat or at a user-identified path, with relevant conversation context. You may read explicitly supplied documents, files, and links to interpret the request. Do not independently search the project, browse for additional sources, evaluate alternatives, or gather evidence answering research questions.

If necessary input is missing or inaccessible, explain what is unavailable and request only what understanding requires. Never claim to have read unavailable material.

Use available host capabilities for reading and saving; no particular tool, service, or credential is required. Report limitations that prevent reading supplied material or persisting the result.

## 2. Analyze Understanding Internally

Evaluate all ten criteria. These are diagnostic checks, not required artifact fields, fixed clarification categories, or a user questionnaire:

1. **Intent:** Desired achievement and stated motivation.
2. **Problem or need:** Underlying problem, need, or curiosity, where relevant.
3. **Expected understanding or decision:** What the user wants to learn, explain, describe, or decide.
4. **Context:** Whether supplied context suffices to interpret the request.
5. **Scope:** Intended subject, boundaries, and exclusions.
6. **Constraints:** Explicit mandatory requirements, constraints, and preferences.
7. **Ambiguity:** Key terms with materially different interpretations.
8. **Consistency:** Contradictions preventing an accurate restatement.
9. **Assumptions:** Unconfirmed assumptions about intent.
10. **Research suitability:** Investigation or learning versus solely executing an already defined task.

Missing detail is not automatically blocking. Distinguish understanding the request from designing or conducting research.

## 3. Determine Readiness

Once sufficiently understood, assess research suitability first. Clarify unclear suitability when it blocks understanding rather than assuming exclusion. Assign exactly one status:

| Status | Condition and action |
|---|---|
| **NOT AN EXPLORATION** | The understood request has no investigative or learning component. Explain the exclusion, suggest an appropriate workflow, and stop without entering the readiness loop or starting another workflow. A fixed solution alone does not justify exclusion. |
| **CLARIFICATION REQUIRED** | Missing intent, ambiguity, contradiction, or an unavoidable unsupported assumption prevents accurate handoff. Ask necessary blocking questions and reassess after answers. |
| **READY** | Exploration is present; primary intent, subject, and expected outcome are understood; no blocker remains. Present the round checkpoint. Further clarification is voluntary. |

The Readiness Gate passes exactly at `READY`. Readiness, choosing to finish clarification, confirming the restatement, and saving are separate events. Reassess after each round and material correction. An explicitly deferred blocker retains `CLARIFICATION REQUIRED`; a nonblocking deferral may accompany `READY`.

### Blocker Test

Before assigning `READY` or classifying a question as blocking, apply all three checks internally to each material uncertainty:

1. **Unresolved meaning:** Identify two plausible interpretations grounded in the input and how they change subject, scope, or outcome. For missing primary intent or conflicting requirements, identify what cannot be understood or reconciled instead of inventing alternatives.
2. **Unavoidable choice:** Identify the unsupported assumption or user decision needed for handoff. Explain why its absence would convey materially different tasks; an effect on research framing, findings, or implementation alone is insufficient.
3. **Faithful handoff:** Can the uncertainty remain open while conveying the same understood task and preserving stated conditions? Available funds are not automatically a spending cap; a desired date is not automatically a deadline. Neither a broad umbrella paraphrase nor silently delegating unknown intent to research resolves ambiguity.

Only a failure to hand off accurately makes the question blocking. Ask those questions before `READY`; otherwise retain the gap without inventing an answer. These checks are internal, not output fields or questions to ask verbatim.

Reclassify only for new information, a correction, or an identified earlier oversight, explaining the concrete reason. When correcting a readiness error, identify the missed ambiguity, contradiction, or assumption. A request for more questions alone does not invalidate `READY` or make optional gaps blocking.

### Nonblocking Gaps

- **Brief preparation:** Leave research framing to brief creation and validation. Related request conditions may be clarified voluntarily, but are not required to finish. Preserve stated decisions affecting the brief; do not design research or compile a separate brief-preparation question list for the artifact, even under another name.
- **Exploration:** Leave facts, explanations, comparisons, and findings to research. Preserve already identified questions that add material meaning beyond the confirmed request.

For each material gap left open in completed input, identify why it does not obscure intent. An unanswered question or a research-question label does not establish delegation to research; clarify delegation when it changes the task. Conversely, do not require the user to choose what research is intended to compare or inform.

Ask neither already answered questions nor questions that would not change understanding. Optional gaps and unselected categories do not block readiness merely because they affect eventual research.

## 4. Run User-Controlled Clarification Rounds

Initially, group related blockers and prioritize those most affecting understanding. Ask specific, understandable questions without dropping necessary distinctions to reduce question count. Label any proposed interpretation or assumption as unconfirmed.

A round includes a related group of questions, responses, and necessary follow-up under [the dialogue protocol](references/clarification-dialogue.md). Once each question has an accepted answer or explicit deferral, incorporate results, reassess readiness, and present a checkpoint. Requests to change direction or stop interrupt the round. Also present a checkpoint when the initial input is already `READY`.

Derive categories from the current request and answers. Offer one only if clarification could materially change understanding of outcome, context, boundaries, conditions, or preferences. Use understandable names and explain what each would clarify. Remove answered or irrelevant categories and add newly discovered ones; do not invent categories to prolong the conversation.

Identify and prioritize blocking clarification. Ask optional questions only when the user selects that direction, using a coherent group rather than every candidate question. Future research is not a category of answers the user must supply; clarify its intended scope only when needed.

### Round Checkpoint

At each checkpoint:

1. Briefly summarize understanding, material changes, and remaining blockers.
2. Offer a manageable, prioritized selection of relevant remaining categories with their purpose, distinguishing blocking from optional clarification. Allow another user-supplied direction; the displayed categories are not exhaustive.
3. Ask whether to deepen a category, introduce another direction, or finish clarification and fix the current results. Wait for an actual choice before optional questions or final restatement. Silence, an empty message, or a skipped answer is not a choice to finish or confirm.

Category selection chooses a topic, not an answer or solution. After its round, repeat the checkpoint. If no useful categories remain, offer finishing or a user-supplied direction without manufacturing questions. Checkpoints occur at dialogue boundaries, not after internal reading, analysis, or saving.

- **Finish at `READY`:** Proceed to restatement. Finishing deepening does not confirm the restatement.
- **Finish with blockers:** Explain why finalization is unavailable. Offer focused clarification, explicitly incomplete saving, or stopping without saving. Incomplete saving proceeds through sections 5 and 6 without changing readiness or claiming completion.
- **Stop without saving:** Leave the workflow incomplete without repeatedly requesting the same answer.

## 5. Restate and Obtain Confirmation

For completed input, after the user chooses to finish at `READY`, restate the request in your own words, incorporating material answers and boundaries from all rounds. Distinguish confirmed information, unconfirmed proposals, and explicit deferrals. Discussing a nonblocking gap does not require including it in the artifact.

For explicitly chosen incomplete saving, restate only the understood portion, label it incomplete and not ready for brief creation, and identify unresolved blockers and intentional deferrals. Ask the user to confirm the partial understanding and recorded gaps; that confirmation does not resolve them.

Ask separately whether the restatement accurately reflects intent. The finish choice is not confirmation. Confirmation validates the presented understanding, not research readiness or a brief; it does not answer unasked questions, resolve omitted ambiguities, or turn separately labeled proposals into requirements or deferrals into research assignments.

After corrections, update the interpretation, reassess affected conditions, and obtain confirmation of the revised restatement. Material corrections invalidate prior confirmation and return to clarification. A newly discovered blocker also returns completed input to clarification, even after broad confirmation. For incomplete input, retain acknowledged blockers and confirm any revised partial restatement.

Without confirmation, do not claim completion. Distinguish unresolved input from `READY` input awaiting confirmation.

## 6. Save the Clarified Input

After confirmation, read [the clarified input template](references/clarified-input-template.md), prepare the applicable variant, and apply its completion checks. The artifact must convey current confirmed understanding without reconstructing the conversation or original input; do not invent content or expand it into a brief, research plan, or findings.

Use the user's destination or the host's configured saving convention. If neither exists, request a destination when saving becomes necessary. Do not overwrite an existing artifact without authorization.

If persistence fails or is unavailable, provide the prepared content in chat, explain that it was not saved, and identify the outstanding saving step. Do not claim persistence or completion.

- **Completed input:** Complete the workflow only when input is `READY`, the current restatement is confirmed, and the result is saved. Report the saved location.
- **Incomplete input:** Report the saved location, remaining blockers, and `CLARIFICATION REQUIRED` status. State that clarification remains incomplete and the document is not ready for brief creation; confirmation and saving do not satisfy completion.

End this stage without automatically creating a brief or starting research.
