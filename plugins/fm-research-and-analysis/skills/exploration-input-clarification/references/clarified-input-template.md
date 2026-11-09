# Clarified Input Template

Read after confirmation and before preparing the Markdown artifact. This resource defines output, not additional questions or readiness criteria; [SKILL.md](../SKILL.md) owns saving and workflow completion.

## Document Structure

Use these exact English headings in this order. `Confirmed request` is required; other sections appear only when they have material content. Omit empty sections and subsections without placeholders such as “not specified.” Do not ask questions or invent content to fill them. Replace bracketed instructions and remove unused headings.

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

Use exactly one H1: a short descriptive phrase derived from the current confirmed request, identifying its subject and desired understanding, explanation, or decision. Include a boundary when omitting it would describe a different or overly broad task. Revisit the title after material corrections.

The title must be noticeably shorter than the full request and must not introduce an unstated technology, solution, finding, or goal. It does not replace the full formulation or need every condition. Use no generic prefix such as “Clarified input”; no mandatory numbering or word count applies.

## Complete and Incomplete Input

| Variant | Required content |
|---|---|
| Completed input | `Confirmed request` contains a complete, coherent statement of the understood task. No blocking assumption or ambiguity may remain, including in an optional section. Nonblocking explicit deferrals may remain. |
| Incomplete input | Only after the user chooses incomplete saving and separately confirms the partial restatement and gaps. `Confirmed request` contains only the understood portion, with its limitations. In `Context, decisions, and boundaries`, identify each unresolved blocker, the missing clarification, and any explicit deferral. If primary intent is unknown, say so instead of inventing it. |

Incomplete input keeps the same headings and order. Immediately after the H1, insert this exact notice:

```markdown
> Status: INCOMPLETE — CLARIFICATION REQUIRED. Not ready for brief creation.
```

Only the incomplete variant may retain blockers. They are known gaps, not a brief-preparation checklist or permission to choose an interpretation. Confirmation does not resolve them or complete clarification. All shared filling and completion checks below apply to both variants.

## Filling Rules

- Write the confirmed request as a paragraph. Incorporate the current material meaning of answers from every round directly into the request, context, or conditions so the artifact stands alone.
- Use separate bullets for independent decisions, conditions, proposals, and questions, keeping qualifications with each item. Keep mandatory conditions and preferences separate and preserve their original force.
- Put necessary context, decisions, boundaries, and exclusions in `Context, decisions, and boundaries`. Attribute user assertions where needed rather than presenting them as verified facts. A reference to supplied material that is itself the subject may remain here.
- Record each current explicit deferral here too: topic, clarification intentionally unanswered, and the user's deferral decision. Preserve the decision, not question identifiers or a dialogue log. Incorporate later answers and omit superseded deferrals. An omitted answer alone is not a deferral; neither omission nor deferral creates a condition, default, or automatic research assignment.
- Put mandatory conditions and preferences under their respective H3 headings; omit their parent H2 when both are empty. A material condition may also appear briefly in the title or request without changing its meaning.
- Include only previously raised, material unconfirmed assumptions or proposals needed for accurate handoff. Label each status explicitly in words, not through placement or emphasis alone. Restatement confirmation does not turn separately labeled proposals into requirements. Do not brainstorm here; blockers belong only in the incomplete variant's context section.
- Include only previously identified research questions about facts, explanations, or choices left to research that add meaning beyond the confirmed request. Explain for each question or homogeneous group why it may remain open without obscuring intent. Do not invent questions, methods, or a work plan, or reclassify brief-framing and organizational details to retain them.
- Exclude original utterances, question-and-answer history, superseded interpretations, phase logs, internal diagnostic checks, checkpoints, and inventories of unselected categories. A source link must not substitute for incorporating the current meaning.
- Exclude a separate brief-preparation question list, even under another name, while preserving stated decisions and conditions affecting a future brief. Do not include a brief, research plan, or findings.

## Completion Checks

Before saving, verify that:

- The artifact is understandable without chat history or reconstruction from original input, and preserves all material current clarifications, conditions, and explicit deferrals with their correct status.
- It meets the selected variant's requirements: a complete request without blockers, or confirmed partial understanding with the exact incomplete notice and visible blockers.
- Exactly one descriptive H1 and applicable fixed H2/H3 headings appear in order. A simple completed request may need only the title and `Confirmed request`.
- No history, disguised source-input section, or brief-preparation question list remains; removing these has not removed material current meaning.
- Passing the Markdown content to the next agent conveys the same meaning as the saved artifact. Formatting alone does not establish a model's interpretation; that requires behavioral verification.

Showing content in chat or stdout is not successful persistence. Apply the saving and completion conditions in `SKILL.md`.
