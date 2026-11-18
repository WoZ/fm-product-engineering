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

Read the [input readiness criteria](../../references/exploration/input-readiness-criterias.md) before the first readiness assessment. Apply them to the current understanding of the request after reading the input, after each round, and after each material correction.

## 3. Determine Readiness

Once sufficiently understood, assess research suitability first. Clarify unclear suitability when it blocks understanding rather than assuming exclusion. Assign exactly one status:

| Status | Condition and action |
|---|---|
| **NOT AN EXPLORATION** | The understood request has no investigative or learning component. Explain the exclusion, suggest an appropriate workflow, and stop without entering the readiness loop or starting another workflow. A fixed solution alone does not justify exclusion. |
| **CLARIFICATION REQUIRED** | A required research mode or project-source boundary is unresolved, or missing intent, ambiguity, contradiction, or an unavoidable unsupported assumption prevents accurate handoff. Ask necessary blocking questions and reassess after answers. |
| **READY** | Exploration is present, primary intent, subject, and expected outcome are understood, each applicable research mode and required project-source boundary is determined, and no blocker remains. Present the round checkpoint. Further clarification is voluntary. |

The Readiness Gate passes exactly at `READY`. Readiness, choosing to finish clarification, confirming the document, and saving are separate events. Reassess after each round and material correction. An explicitly deferred blocker retains `CLARIFICATION REQUIRED`; a nonblocking deferral may accompany `READY`.

If the goal or subject is unclear, clarify it before asking about research mode. Ask separate blocking questions about the mode and the project-source boundary if both are unresolved. Frame mode options in terms of what to investigate. For sources, offer relevant choices such as task-relevant materials, named paths or materials, or only the project materials the user supplied. Apply the dialogue protocol, including its custom-answer option. Use already clear decisions without asking again.

Reclassify only for new information, a correction, or an identified earlier oversight, explaining the concrete reason. When correcting a readiness error, identify the missed ambiguity, contradiction, or assumption. A request for more questions alone does not invalidate `READY` or make optional gaps blocking.

## 4. Run User-Controlled Clarification Rounds

Initially, group related blockers and prioritize those most affecting understanding. Ask specific, understandable questions without dropping necessary distinctions to reduce question count. Label any proposed interpretation or assumption as unconfirmed.

A round includes a related group of questions, responses, and necessary follow-up under [the dialogue protocol](references/clarification-dialogue.md). Once each question has an accepted answer or explicit deferral, incorporate results, reassess readiness, and present a checkpoint. Requests to change direction or stop interrupt the round. Also present a checkpoint when the initial input is already `READY`.

Derive categories from the current request and answers. Offer one only if clarification could materially change understanding of outcome, context, boundaries, conditions, or preferences. Use understandable names and explain what each would clarify. Remove answered or irrelevant categories and add newly discovered ones; do not invent categories to prolong the conversation.

Identify and prioritize blocking clarification. Ask optional questions only when the user selects that direction, using a coherent group rather than every candidate question. Future research is not a category of answers the user must supply; clarify its intended scope only when needed.

### Round Checkpoint

At each checkpoint:

1. Briefly summarize understanding, material changes, and remaining blockers.
2. Offer a manageable, prioritized selection of relevant remaining categories with their purpose, distinguishing blocking from optional clarification. Allow another user-supplied direction; the displayed categories are not exhaustive.
3. Ask whether to deepen a category, introduce another direction, or finish clarification and fix the current results. Wait for an actual choice before optional questions or the final document preview. Silence, an empty message, or a skipped answer is not a choice to finish or confirm.

Category selection chooses a topic, not an answer or solution. After its round, repeat the checkpoint. If no useful categories remain, offer finishing or a user-supplied direction without manufacturing questions. Checkpoints occur at dialogue boundaries, not after internal reading, analysis, or saving.

- **Finish at `READY`:** Prepare the document preview and ask for separate confirmation.
- **Finish with blockers:** Explain why finalization is unavailable. Offer focused clarification, explicitly incomplete saving, or stopping without saving. Incomplete saving proceeds through sections 5 and 6 without changing readiness or claiming completion.
- **Stop without saving:** Leave the workflow incomplete without repeatedly requesting the same answer.

## 5. Preview the Document and Obtain Confirmation

After the user chooses to finish at `READY` or explicitly chooses incomplete saving, read the [input template](../../references/exploration/input-template.md). Resolve the file's prose language using instructions for the save destination and any compatible user choice, defaulting to the dialogue language. Prepare the Markdown in that language with the template's fixed English headings and applicable notice. Compare it with the dialogue for faithful coverage of the current intent, decisions, restrictions, and explicit deferrals.

For a completed candidate, follow [isolated validation](../../references/exploration/isolated-validation.md). Run the validator in a fresh agent context without the clarification history. Require a `PASS` for this exact Markdown before showing the full confirmation preview. Fix document defects and recheck. Return to clarification when a material decision remains unresolved. If isolated execution is unavailable, use the new-chat handoff and wait for the report before requesting confirmation.

For an explicitly requested incomplete candidate, check the incomplete variant directly against the input template and the dialogue. Verify that the document contains the understood portion, the incomplete notice, every known blocker, and each explicit deferral. Correct format errors and missing or misrepresented content, then repeat the check. This path permits confirmation of incomplete saving with the blockers visible. The document remains incomplete for downstream use.

Show the full document in the dialogue language using the [document preview format](references/clarification-dialogue.md#preview-the-document-for-confirmation). Localize the title, section headings, and any incomplete notice for the preview. Tell the user which language will be used for the file.

Ask the user to confirm the entire displayed document for saving in the stated language. Confirmation applies to the displayed version, including the status of any proposals, deferrals, and unresolved blockers. After a correction, reassess readiness, validate the revised candidate, show the full revised preview, and obtain confirmation again. If a new blocker emerges, return to clarification before seeking confirmation of completed input.

Without confirmation, do not claim completion. Distinguish unresolved input from `READY` input awaiting confirmation.

## 6. Save the Clarified Input

Save the confirmed document. When the file language differs, translate the confirmed text faithfully, preserving its section order, content, and the force of every decision and condition. Use the template's fixed headings and notice where applicable, and omit chat presentation elements. Check the file against both the confirmed preview and the template before writing. If the destination requires a different language from the one announced, or any content needs to change, return to section 5 for validation and a new confirmation before saving.

Use the user's destination or the host's configured saving convention. If neither exists, request a destination when saving becomes necessary. Do not overwrite an existing artifact without authorization.

If persistence fails or is unavailable, provide the prepared content in chat, explain that it was not saved, and identify the outstanding saving step. Do not claim persistence or completion.

- **Completed input:** Complete the workflow only when input is `READY`, the current document is confirmed, and the result is saved. Report the saved location.
- **Incomplete input:** Report the saved location, remaining blockers, and `CLARIFICATION REQUIRED` status. State that clarification remains incomplete and the document is not ready for downstream use; confirmation and saving do not satisfy completion.

End this stage without automatically creating a brief or starting research.
