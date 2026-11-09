# Clarification Dialogue Protocol

Read before asking the first question of any kind. This protocol governs presentation and answer handling; [SKILL.md](../SKILL.md) owns readiness, round checkpoints, confirmation, and workflow completion.

## Present Questions

Present every question as Markdown text in chat and receive answers as chat messages. Apply these rules to clarification, checkpoint menus, confirmation, missing-input requests, and saving destinations:

- Present a related group in one message. Start each question with `❓ **Q1 — Topic:** Question text`, using a stable identifier and short topic label. Localize wording to the conversation language.
- List choices as Markdown bullets with literal letter identifiers and only those letters bold: `- **A.** Choice text`. Separate question blocks with a horizontal rule or equivalent clear spacing.
- End every choice list with a separate custom-answer option using the next unused letter and an explicit instruction to enter an answer, such as `C. Custom answer — enter your own response.` A prompt-level invitation is insufficient. With no meaningful predefined choices, specify the information needed and show only `A. Custom answer — enter your own response.` rather than inventing alternatives.
- Give brief implications where useful for choosing, including leaving a choice open for exploration where relevant. Use the question heading, choices, and reply example as the visual structure, without appended arrow-marked rationale lines. Explain further when requested or needed to resolve an insufficient answer.
- Request a separate answer for each question by identifier. Multiple answers may share one message. Include a reply example such as `Q1: A` and `Q2: C — <custom text>`; do not invite one undifferentiated response for the group.
- Keep identifiers and option meanings stable on retries. A materially changed question receives a new identifier. Revisit an accepted answer only when a correction or conflict requires it.

Illustrative layout; derive actual questions from the request and localize the wording:

```markdown
❓ **Q1 — Funding:** What does the available budget represent?

- **A.** The total project spending limit.
- **B.** Currently available funds; additional funding is possible.
- **C.** Custom answer — enter your own response.

---

❓ **Q2 — Participation:** Is your personal participation required?

- **A.** Yes.
- **B.** No.
- **C.** Custom answer — enter your own response.

Answer each question separately, for example:
Q1: C — <your explanation>
Q2: B.
```

Before presenting any question, check it against the format above, including its heading, bold letters, final custom-answer option, and separately identified reply example.

## Validate Answers and Handle Deferrals

Evaluate every response semantically, including custom text and qualifications accompanying a letter. Judge whether it answers the requested distinction, not its length, factual proof, or the feasibility of the user's wishes.

| Response | Action |
|---|---|
| Clear letter selection, custom answer, or qualified selection | Associate it with its question and preserve the whole meaning. A bare valid letter is sufficient. Accept clear custom answers that correct the offered choices. Preserve qualifications rather than favoring a contradictory letter. |
| Unclear question-to-answer mapping | Ask the user to identify the corresponding questions; do not move an answer to another question. |
| Missing, off-topic, contradictory, or ambiguous answer | Retain accepted answers from the group. Briefly identify the unresolved point and re-ask only the affected question with its original identifier. Repeat after each insufficient response, waiting for an answer between attempts, until answered or explicitly deferred. |
| Custom-answer letter without text | Treat as unanswered, not a substantive answer. |
| Request to explain, revise the task, change direction, or stop | Treat as dialogue control: respond and reassess pending questions rather than classifying it as an invalid answer. |
| On-topic “I don't know” or “I haven't decided” | Unless the next action is explicit, clarify whether the user wants an explanation, intentional deferral, or a choice left to exploration. Lack of knowledge establishes none of these by itself. |
| Explicit skip or deferral | Acknowledge it and stop retrying. Retain the topic, missing clarification, and deferral decision for restatement and saving. Revisit only if the user reopens it or a material change requires reassessment; do not repeatedly reassess to pressure an answer. |

Check each answer against its explanation and relevant prior input. Preserve its force: preferences remain optional, assumptions remain unconfirmed, and skipping supplies no substantive answer. An omitted answer, silence, or empty custom-answer selection is not explicit deferral.

A deferral supplies no default, requirement, or automatic research question. Return to the readiness rules in `SKILL.md`: whether the unanswered issue blocks understanding determines the status, not the act of deferring it.
