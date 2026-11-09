# Clarified Input Template

Read this resource after the user confirms the current restatement and before preparing the final Markdown. It defines the output document, not additional clarification questions or readiness criteria.

## Document Structure

Use the following heading names exactly, in English, and in this order. `Confirmed request` is always required. Include each other section only when it has material content; omit empty sections and subsections entirely, without placeholders such as "not specified." Do not ask questions or invent content to populate the structure.

The bracketed text below describes content to replace. Do not copy these instructions or unused headings into the result.

```markdown
# [Short descriptive title of the confirmed request]

## Confirmed request

[A complete, coherent statement of the user's intent, subject, expected understanding or decision, and material boundaries, incorporating the current meaning of clarifications.]

## Context, decisions, and boundaries

- [Material context, an established decision, a subject boundary, or an exclusion.]

## Mandatory constraints and preferences

### Mandatory constraints

- [A mandatory condition, retaining its original force and qualifications.]

### Preferences

- [A preference, explicitly retaining its nonmandatory status.]

## Unconfirmed assumptions and proposals

- [A material, previously raised nonblocking assumption or proposal, explicitly labeled as unverified or unaccepted.]

## Future research questions

- [A material, previously identified research question, with an explanation of why leaving it open does not obscure the user's intent.]
```

## Title

Form the title from the current confirmed request, rather than the first message. Use one short descriptive phrase identifying the subject and what the user wants to understand, explain, or decide. Include a material boundary if omitting it would describe a different or overly broad task.

The document must have exactly one H1, without a generic prefix such as "Clarified input." No mandatory numbering or word count applies. The title must be noticeably shorter than the full request and must not introduce a technology, solution, finding, or goal the user did not specify. It does not replace the full formulation or need to repeat every condition. Revisit it after a material correction to the request.

## Incomplete Input Variant

Use this variant only after the user chooses to save incomplete input and separately confirms the partial restatement and recorded gaps. Immediately after the H1, insert this exact status notice:

```markdown
> Status: INCOMPLETE — CLARIFICATION REQUIRED. Not ready for brief creation.
```

Keep the same section names and order. In this variant, `Confirmed request` contains only the understood portion confirmed by the user, with its limitations stated explicitly. In `Context, decisions, and boundaries`, identify each unresolved blocker and the clarification still missing, including any explicit deferral decision. If primary intent is not yet understood, say so rather than inventing a complete request. These are known gaps in the current understanding, not a brief-preparation checklist or permission to choose an interpretation.

The complete-request requirement applies to completed input. An incomplete document must instead accurately convey the confirmed partial understanding, conspicuous status, and unresolved blockers. All other filling and completion checks still apply. Confirmation of this variant does not resolve the blockers or complete the workflow.

## Filling Rules

- Write the confirmed request as a paragraph. Use separate bullets for independent decisions, conditions, proposals, and questions; keep explanations and qualifications with their item. Do not combine a mandatory condition and a preference into one item.
- Put necessary context, established decisions, subject boundaries, and exclusions in `Context, decisions, and boundaries`. Attribute user assertions where needed so they are not presented as independently verified facts.
- Preserve each current explicit deferral in `Context, decisions, and boundaries`: identify its topic, the clarification intentionally left unanswered, and the user's decision to defer it. A nonblocking deferral can appear in completed input; an unresolved blocking deferral requires the incomplete variant. Keep the substantive decision rather than question identifiers or a dialogue log. If a later answer resolves the issue, incorporate that answer and omit the superseded deferral.
- Put mandatory conditions and preferences in their respective H3 subsections. Include each H3 only when it has content, and omit their parent H2 if both are empty. Preserve the original strength of each condition. A brief mention of a material condition in the title or confirmed request may supplement its full entry, but must not change its meaning.
- Keep only previously raised, material unconfirmed assumptions or proposals needed to hand off the request accurately. This section is not a place to brainstorm. Label each item's status in words; neither placement nor emphasis alone makes it clear. Confirmation of the restatement does not turn separately labeled proposals into requirements. An assumption that blocks understanding must be resolved before the final document, rather than hidden here.
- Keep only already identified research questions about facts, explanations, or choices left to research that add material meaning beyond the confirmed request. Explain for each question or homogeneous group why it can remain open. Do not invent questions, methods, or a work plan to fill the section. Do not reclassify brief-framing or organizational details as research questions merely to preserve them.
- Preserve the current meaning of material clarifications directly in the request, context, or conditions. Do not include original utterances, a question-and-answer history, superseded interpretations, or a source link as a way to reconstruct that history. A necessary reference to user material that is itself the subject of the request may remain in context.
- Incorporate material answers from every clarification round while preserving their force as requirements, preferences, or unconfirmed proposals. Omit round checkpoints, navigation choices, and inventories of unselected categories. Preserve explicit deferrals as specified above; an omitted answer alone supplies no deferral decision. Deferrals do not supply conditions or automatically become future research questions.
- Do not include a separate list of brief-preparation questions, including under another name. Brief creation determines its own missing details. Already stated decisions and conditions must still be preserved even when they affect the future brief.
- Exclude phase logs, the internal analytical checklist, a brief, a research plan, and research findings.

## Completion Checks

Before saving, verify that:

- The document is understandable without the chat history, preserves all material current clarifications and conditions, and contains a complete confirmed request.
- Exactly one descriptive H1 and the applicable fixed H2/H3 headings appear in the prescribed order. A simple request may need only the title and `Confirmed request`.
- Preferences remain preferences, proposals remain unconfirmed, and user hypotheses are not stated as verified facts. Explicit deferrals remain unanswered, without default values or automatic research assignments. No blocking ambiguity is concealed in an optional section; unresolved blockers appear only in the visibly incomplete variant.
- No history, disguised source-input section, or list of brief-preparation questions remains. Removing them has not removed material current information.
- Saving the Markdown or passing its content to the next agent conveys the same meaning. Formatting alone does not guarantee a particular model's interpretation; that requires behavioral verification.

Apply the saving and completion conditions in `SKILL.md`. Showing this content in chat or stdout does not itself satisfy successful persistence.
