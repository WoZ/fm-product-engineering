---
name: exploration-input-clarification
description: Clarify a user's exploration request and save confirmed input for research brief creation. Use for requests to learn, explain, describe, understand, or inform a decision in any subject. Excludes brief creation, research execution, and requests solely to carry out an already defined task.
---

# Exploration Input Clarification

Establish a shared understanding of the user's request and save clarified input for brief creation. Exploration can concern any subject; it does not require choosing between solutions. A selected solution can still be explored for its behavior, risks, or use within the user's stated boundary.

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
7. **Ambiguity:** Are there materially different interpretations of the user's intent?
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
| **CLARIFICATION REQUIRED** | At least one blocking issue remains: you cannot accurately restate intent without an unsupported assumption or choice on the user's behalf. Ask the necessary blocking questions and reassess after answers. |
| **READY** | The request includes exploration, its primary intent and intended subject are understood, and no blocking issue remains. Skip clarifying questions and proceed to restatement. |

The Readiness Gate passes exactly at `READY`. It assesses input readiness only; confirmation and saving are separate completion conditions. Open questions for brief preparation or exploration do not prevent `READY` unless they block understanding at this stage.

### Decide What Must Be Asked Now

A question is blocking only if its answer is needed to understand and accurately restate the user's intent before handing input to brief creation. You must clarify an issue unresolved by the supplied context when:

- The primary intent cannot be determined.
- Materially different interpretations would produce different restatements.
- Conflicting requirements prevent a coherent understanding.
- An unknown preference, constraint, or user decision would otherwise have to be assumed to interpret the request.

Defer material nonblocking gaps, preserving them for the next stage:

- **Brief preparation:** Research-framing details that can be clarified while creating and validating the brief.
- **Exploration:** Facts, explanations, comparisons, and findings to establish through research.

You must not ask deferred questions now merely because their answers affect eventual research. Do not ask questions already answered in the input or questions that would not change your understanding. Do not ask the user to choose between alternatives when comparing them is the requested research.

An uncertainty does not become deferrable merely because it can be phrased as a research question. Clarify unknown user intention when it blocks understanding; leave open a decision the user wants research to inform.

Group related blocking issues, prioritize those most affecting understanding, and ask specific, understandable questions. You should ask the minimum number needed and offer meaningful options with brief implications when useful. Reassess affected issues after answers. You may propose interpretations or assumptions, but label them as unconfirmed proposals and never treat them as user requirements without confirmation.

If the user cannot or does not want to answer, reassess whether the question is genuinely blocking. Defer it if nonblocking. If it remains blocking, explain the unresolved issue and leave the workflow incomplete; do not repeatedly ask the same question or invent an answer.

## 4. Restate and Obtain Confirmation

At `READY`, restate the request in your own words, including material stated boundaries. Clearly distinguish confirmed information, unconfirmed proposals, and deferred questions.

Ask the user to confirm that the restatement accurately reflects their intent. Do not ask them to certify research readiness or approve a brief. Confirmation of the restatement must not silently turn separately labeled proposals into confirmed requirements.

If the user corrects the interpretation, update it, reassess affected conditions, and obtain confirmation of the revised restatement. Return to clarification only if a blocking issue remains.

If the user stops or does not confirm, do not claim completion. Distinguish unresolved input from input that is `READY` but awaiting confirmation.

## 5. Save the Clarified Input

After confirmation, prepare and save clarified input for brief creation containing:

- The confirmed restatement of the request.
- The original input or an accessible reference for the next stage, preserving material user clarifications.
- Stated decisions, boundaries, exclusions, mandatory constraints, and preferences, keeping their meanings distinct.
- Material unconfirmed assumptions or proposals, explicitly labeled.
- Material open questions, distinguished as brief-preparation questions or exploration questions.

Do not invent content to fill empty categories or expand the artifact into a brief, research plan, or findings.

Use the user's specified destination or the host's configured artifact-saving convention. If neither exists, request a destination when saving becomes necessary. Do not overwrite an existing artifact without authorization.

If saving fails or the host cannot persist artifacts, provide the prepared content in chat, explain that it was not saved, and identify the outstanding saving step. Do not claim persistence or completion.

Complete the workflow only when all three conditions hold: input is `READY`, the user has confirmed the current restatement, and the result has been saved. Report the saved location to the user. End this stage without automatically creating a brief or starting research.
