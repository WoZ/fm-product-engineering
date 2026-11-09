---
name: exploration-input-clarification
description: Clarify a user's exploration request and save confirmed input for research brief creation. Use for requests to learn, explain, describe, understand, or inform a decision in any subject. Excludes brief creation, research execution, and requests solely to carry out an already defined task.
---

# Exploration Input Clarification

Establish a shared understanding of the user's request through user-controlled clarification rounds and save confirmed input for brief creation. Exploration can concern any subject; it does not require choosing between solutions. A selected solution can still be explored for its behavior, risks, or use within the user's stated boundary.

This stage must not create a research brief, fully specify or plan the research, or conduct research. Brief creation has its own analysis, clarification, and validation. Details may remain open when they do not prevent understanding the user's intent.

## 1. Read the Supplied Input

Use the input supplied in chat or at a user-identified file path, together with relevant conversation context, before asking questions. You may read documents, files, and links explicitly supplied to help interpret the request. You must not independently search the project, browse for additional sources, evaluate alternatives, or collect evidence to answer research questions.

If required input is missing or inaccessible, explain what is unavailable and request only what is necessary to understand the request. Never claim to have read unavailable material.

Use the host's available capabilities for reading and saving; no particular tool, service, or credential is required by this workflow. Report any host limitation that prevents reading supplied material or persisting the result.

## 2. Analyze Understanding Internally

Evaluate all of these criteria internally. They are checks for understanding, not required artifact fields or a questionnaire for the user:

1. **Intent:** What does the user want to achieve, and is their stated motivation understood?
2. **Problem or need:** What problem, need, or curiosity underlies the request, where relevant?
3. **Expected understanding or decision:** What does the user want to learn, explain, describe, or decide?
4. **Context:** Is the supplied context sufficient to interpret the request?
5. **Scope:** Are the intended subject and stated boundaries and exclusions clear?
6. **Constraints:** What mandatory requirements, constraints, and preferences has the user explicitly stated?
7. **Ambiguity:** Do key terms leave materially different interpretations of the subject, scope, or expected outcome unresolved?
8. **Consistency:** Do contradictions prevent an accurate restatement?
9. **Assumptions:** Does the interpretation depend on an unconfirmed assumption about intent?
10. **Research suitability:** Does the request include investigation or learning, rather than only carrying out an already defined task?

Missing detail is not automatically a blocker. Distinguish information needed to understand the request from information needed to design or conduct research.

Throughout the workflow, incorporate explicit user corrections and changes. You must not replace the stated problem, promote preferences to mandatory constraints, treat hypotheses as facts, impose technologies or implementation approaches, or add research scope. Respect established decisions and restrictions. Do not choose between conflicting requirements unless the supplied context already resolves the conflict.

## 3. Determine Readiness and Clarify Blockers

Once the request is sufficiently understood, assess research suitability first. If suitability itself is unclear in a way that blocks understanding, clarify it instead of assuming the request is outside scope. Assign exactly one status:

| Status | Condition and action |
|---|---|
| **NOT AN EXPLORATION** | The understood request has no investigative or learning component. Explain why it falls outside this workflow, suggest an appropriate next workflow, and end without entering the readiness loop or automatically starting another workflow. A fixed solution alone does not justify this status. |
| **CLARIFICATION REQUIRED** | At least one blocking issue remains: materially different user intentions are unresolved, or understanding requires an unsupported assumption or choice on the user's behalf. Ask the necessary blocking questions and reassess after answers. |
| **READY** | The request includes exploration, its primary intent, intended subject, and expected outcome are understood, and no blocking issue remains. Offer the round checkpoint before proceeding to final restatement; further clarification is voluntary. |

The Readiness Gate passes exactly at `READY`. It assesses input readiness only; choosing to finish clarification, confirming the restatement, and saving are separate steps. Open questions for brief preparation or exploration and unselected optional categories do not prevent `READY` unless they block understanding at this stage. Reassess readiness after each round and material correction.

### Decide What Must Be Asked Now

A broad paraphrase is not sufficient evidence of understanding. Before assigning `READY` or treating a question as blocking, apply these checks internally to each material uncertainty:

1. **Identify the unresolved meaning.** For an ambiguity, name two plausible interpretations grounded in the supplied input and explain how they change the intended subject, scope, or expected outcome. If the issue is missing primary intent or conflicting requirements, identify what cannot be understood or reconciled instead of inventing alternative intentions.
2. **Identify the unavoidable choice.** State the assumption or user decision that handing off the request would require without an answer. An effect on research framing, findings, or implementation alone is insufficient; explain why the next stage would otherwise receive materially different tasks.
3. **Try a faithful handoff without that choice.** Check whether the uncertainty can remain open while preserving the same understood task and the original force of stated conditions. For example, available funds are not automatically a spending cap, and a desired completion date is not automatically a deadline. A broad umbrella statement that hides different intentions does not pass this check. Neither does silently treating unknown intent as a choice delegated to research.

A question is blocking only when these checks show that missing intent, a material ambiguity, a contradiction, or an unavoidable unsupported assumption prevents an accurate handoff. Ask the necessary questions before assigning `READY`. Otherwise, leave the gap nonblocking without inventing an answer. These checks are internal reasoning aids, not required artifact fields or a questionnaire.

Keep classifications grounded in the current input. A request to identify more gaps or ask more questions does not itself make a nonblocking gap blocking or invalidate `READY`. Reclassify when new information, a user correction, or a specifically identified earlier oversight changes the assessment. Explain the concrete reason to the user; when correcting an earlier readiness error, identify the missed ambiguity, contradiction, or assumption rather than relabeling the whole category.

Distinguish nonblocking gaps from required clarification:

- **Brief preparation:** Leave research-framing work to brief creation and validation. A user may voluntarily clarify a related condition of their request during deepening, but do not design the research or require this answer to finish. Do not compile or save a separate list of brief-preparation questions in the final artifact, including under another category. Preserve any already stated decisions or conditions that affect the brief.
- **Exploration:** Preserve material, already identified questions about facts, explanations, comparisons, and findings for the final artifact when they add meaning beyond the confirmed request.

Do not require answers to nonblocking questions merely because they affect eventual research. Offer relevant optional clarification through the deepening loop below. Do not ask questions already answered in the input or questions that would not change your understanding. Do not ask the user to choose between alternatives when comparing them is the requested research.

Before deferring a material gap, identify why leaving it open does not obscure the user's intent. Phrasing an uncertainty as a research question does not make it deferrable, and an unanswered question is not evidence that the user wants to explore its alternatives. Clarify whether a choice is delegated to research when that distinction changes the intended task.

For the initial clarification round, group related blocking issues, prioritize those most affecting understanding, and ask specific, understandable questions. Do not skip necessary distinctions to minimize the question count. Use the question presentation rules below. You may propose interpretations or assumptions, but label them as unconfirmed proposals and never treat them as user requirements without confirmation.

If the user cannot or does not want to answer, reassess whether the question is genuinely blocking. Defer it if nonblocking. If it remains blocking, explain the unresolved issue and leave the workflow incomplete; do not repeatedly ask the same question or invent an answer.

## 4. Offer User-Controlled Deepening

A round consists of a related group of questions and the user's responses. After every round, incorporate the answers, reassess readiness, and present a checkpoint. Also present a checkpoint when the initial input is already `READY`; optional questions are never a prerequisite for ending clarification. Requests classified as `NOT AN EXPLORATION` exit under section 3 without entering this loop.

### Derive Relevant Categories

Derive possible clarification categories from the current request and answers. Propose a category only when its clarification could materially change understanding of the desired outcome, context, boundaries, conditions, or preferences. Name it in terms the user can understand and briefly explain what clarifying it would change.

Generate categories for the current task rather than using a fixed questionnaire or domain-specific catalog. The internal understanding criteria are diagnostic aids, not categories that every user must fill. Remove answered or irrelevant categories and add newly discovered ones after each round. Do not invent categories to prolong the conversation or treat selection of a category as acceptance of an answer or solution.

Distinguish:

- **Blocking clarification:** Needed to distinguish the intended task or resolve a contradiction. Identify it explicitly and prioritize it.
- **Optional clarification:** Could enrich the request, but can remain unanswered without obscuring intent. Ask it when the user selects that direction.
- **Future research:** Calls for facts, explanations, comparisons, or findings. Leave the answer to research; clarify the user's intended scope only when needed.

An unknown user intention must not be disguised as a future research question. Conversely, a choice the user wants research to inform must not become a required user decision.

### Present Questions

Use the host's available structured question interface when available and permitted, with meaningful answer choices or free-text input. Give brief implications where they help the user choose. Allow a custom answer; where relevant, allow the user to leave a choice open for exploration. If no suitable structured interface is available, use a concise text menu or free-text question with the same semantics. When running in Codex, read [Codex interaction guidance](references/codex-interaction.md) before presenting the first questions.

Within a selected category, ask a coherent group of questions, then return to the checkpoint. Do not automatically ask every candidate question. Preserve the force of each answer: a preference remains optional, an assumption remains unconfirmed, and skipping a question supplies no answer. Revisit an answered question only when a correction or conflict makes it necessary.

### Round Checkpoint and User Choice

At each checkpoint:

1. Briefly summarize current understanding and material changes, and identify any remaining blockers.
2. Offer the relevant remaining categories with their purpose, distinguishing blocking and optional clarification. Show a manageable prioritized selection and allow the user to introduce another direction; do not imply the displayed set is exhaustive.
3. Explicitly ask whether to deepen a selected category, introduce another direction, or finish clarification and fix the current results. Wait for the user's choice before asking optional questions or proceeding to final restatement. Silence, a dismissed menu, or a skipped answer is not a choice to finish or confirm.

If the user chooses a direction, conduct the next round and repeat the checkpoint. If no useful categories remain, offer finishing or a user-supplied direction without manufacturing more questions. These checkpoints occur at dialogue boundaries, not after internal reading, analysis, or saving operations.

If the user chooses to finish at `READY`, proceed to section 5. This choice ends deepening; it does not confirm the final restatement. If blockers remain, explain why finalization is unavailable and offer focused clarification or stopping without completion. Do not save an unfinished final artifact. If the user stops, leave the workflow incomplete without repeatedly requesting the same answer.

## 5. Restate and Obtain Confirmation

After the user chooses to finish clarification at `READY`, restate the request in your own words, including material stated boundaries and answers from all rounds. Clearly distinguish confirmed information, unconfirmed proposals, and any deferred questions discussed during clarification. Discussing a nonblocking gap does not make it a required artifact field; brief-preparation questions must not become a final handoff list.

Ask the user separately to confirm that the restatement accurately reflects their intent. Do not reuse the choice to finish clarification as confirmation. Do not ask them to certify research readiness or approve a brief. Confirmation validates the presented restatement; it does not resolve omitted ambiguities, answer unasked questions, or turn separately labeled proposals into confirmed requirements.

If the user corrects the interpretation, update it, reassess affected conditions, and obtain confirmation of the revised restatement. A material correction returns to the clarification loop and invalidates prior confirmation. If a blocking ambiguity is discovered, return to clarification even if the user has already confirmed a broad restatement.

If the user stops or does not confirm, do not claim completion. Distinguish unresolved input from input that is `READY` but awaiting confirmation.

## 6. Save the Clarified Input

After confirmation, read [the clarified input template](references/clarified-input-template.md) and prepare the Markdown document using its structure and filling rules. The document must convey the current confirmed intent without requiring the next agent to reconstruct it from the conversation or original input. Incorporate the material meaning of user clarifications, decisions, boundaries, exclusions, constraints, and preferences directly into the appropriate sections.

Before saving, check the document against the template's completion checks. Do not invent content to fill empty categories or expand the artifact into a brief, research plan, or findings.

Use the user's specified destination or the host's configured artifact-saving convention. If neither exists, request a destination when saving becomes necessary. Do not overwrite an existing artifact without authorization.

If saving fails or the host cannot persist artifacts, provide the prepared content in chat, explain that it was not saved, and identify the outstanding saving step. Do not claim persistence or completion.

Complete the workflow only when all three conditions hold: input is `READY`, the user has confirmed the current restatement, and the result has been saved. Report the saved location to the user. End this stage without automatically creating a brief or starting research.
