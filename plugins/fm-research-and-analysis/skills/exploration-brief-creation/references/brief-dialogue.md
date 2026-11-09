# Brief Dialogue Protocol

Read before any question. [SKILL.md](../SKILL.md) owns mode permission, readiness, confirmation, and saving; this reference governs presentation and answer handling.

## Present Questions

- Ask in Markdown chat and receive answers as chat messages. Localize the wording to the conversation language.
- Start each question with `❓ **Q1 — Topic:** Question text`, assigning stable identifiers and short topic labels.
- Group related questions in one message, with clear spacing between blocks. Present options as bullets with literal letter identifiers: `- **A.** Choice text`.
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

## Handle Answers

- Accept a clear letter, custom response, or qualified choice. Preserve qualifications; a response allowing documents only does not allow code inspection.
- Retain accepted answers. For ambiguous mapping or an unanswered, contradictory, or off-topic response, explain the specific gap and re-ask only the unresolved question. An empty custom answer supplies no answer.
- Treat requests for explanation, corrections, stopping, or changes of direction as dialogue control. Incorporate corrections and reassess affected decisions.
- For “I don't know,” clarify whether explanation, explicit deferral, or assignment to research is intended when the next action is unclear. Do not infer any of these from silence or uncertainty.
- Honor explicit deferrals without repeated retries. Record material effects, but do not convert a skipped decision into a default or research permission. Deferring project-context selection leaves the mode unselected and discovery unavailable.
- Keep confirmation separate from choosing to finish. Ask whether the presented complete brief is accurate and accepted; after material changes, confirm the updated document.

Before sending any question, check its identifier, option letters, final custom-answer option, and reply example.
