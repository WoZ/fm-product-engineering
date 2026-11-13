# `Topic And Context`

Use this reference when establishing the topic and relevant context for `Topic And Context`. Use the definitions and terminology rules in [the skill's terms](../SKILL.md#terms). Apply this guidance alongside the shared workflow in `SKILL.md`.

## Phase Logic

- **Topic and available context.** Use the topic, supplied materials, and relevant conversation context.
- **Initial checks.** At invocation, the first `Phase Agent Check Set` uses the available initial input. Check whether a topic is present and, when one is present, whether its meaning and the available context are sufficient for the next step.
- **Missing topic.** If no topic can be identified, use that check result to formulate a `Phase Agent Action Proposal` asking for the topic. When a topic is present, use the clarity and context check results to formulate the appropriate next interaction.
- **Targeted clarification.** When establishing the topic and context, ask only about missing information that materially affects the answer or next step.

## Input Classification

Use the following categories for `Phase Agent Input Classification` in `Topic And Context`, for both initial input and subsequent responses. These are local classification labels; do not assume they apply to other `Skill Phase` contexts.

| Category | Intent | Examples |
|---|---|---|
| **Provide Or Revise Context** | Introduce or extend the topic, provide facts, clarify conditions, correct the agent's understanding, or revise requirements. | "I use Proxmox." / "Exclude cloud solutions." |
| **Express A Decision** | Confirm, select, reject, withdraw a decision, or explicitly defer a choice. | "I choose the second option." / "We will decide the budget later." |
| **Ask A Question** | Request an explanation about the investigation's subject or the skill's behavior. | "What does high availability mean?" / "Why are you asking for confirmation again?" |
| **Request Assistance Or A Result** | Ask for options, help framing the topic, a summary, a document, or a saved result. | "Help me narrow the topic." / "Save the agreed context." |
| **Direct The Interaction** | Change the discussion's format or order, request a phase transition, or pause, resume, or stop work. | "Ask one question at a time." / "Let's move on to research." / "Let's stop." |

Preserve the specific intention within a category. For example, distinguish additional context from a request to replace an agreed condition, and distinguish confirmation from rejection. Identify the subject separately: a question about the investigation and a question about the skill's workflow both fall under **Ask A Question**, but concern different content.

- Identify every expressed intention. One `Phase User Move` may contain several intentions, including several within the same category.
- Associate each intention with the specific content it concerns: what the user confirms, changes, or asks about. Partial confirmation does not accept unrelated proposals.
- Classification does not apply changes or establish readiness for a transition. Use it to select the applicable `Phase Agent Check Set`. A question alone is not a revision request, although the subsequent checks may reveal an error.
- Preserve ambiguity for checking rather than guessing. Describe a clear intention outside these categories directly instead of forcing it into the nearest category.

## Phase Agent Checks

### Request Clarity

Use this `Phase Agent Check` to determine whether the user's request, together with the available context, supports an unambiguous understanding of the expected response or action, its subject, and its scope.

Evaluate:

- **Intent:** Is it clear what the user expects, such as an explanation, revision, confirmation, or another result?
- **Subject:** Is it clear which proposal, requirement, document, statement, or other content the request concerns? Resolve references such as "this option" using the available context.
- **Scope:** Is it clear which parts the request affects and how broadly the requested response or change applies?
- **Relationships:** For compound input, is it clear how the intentions relate? Determine whether confirmation is conditional, a correction replaces an earlier requirement, or a decision depends on an answer. Mark this criterion as not applicable when there are no relationships to evaluate.

Clarification is required when at least two plausible interpretations remain and choosing between them would materially change the next response, action, or recorded decision. A merely conceivable alternative interpretation is not sufficient reason to require clarification.

Record one of these outcomes:

- **Clear:** No material ambiguity remains, or the available context resolves it.
- **Clarification Required:** Material ambiguity remains. Retain the check result, identifying each unresolved criterion from the Evaluate list, the ambiguous content, the plausible interpretations, and why the difference matters.

For example, "Remove the second option" is clear when the immediately preceding discussion contains one relevant numbered list. It requires clarification when several lists remain plausible and the available context does not identify the intended one.

This check evaluates clarity of understanding. It does not establish context completeness, feasibility, or consistency with earlier decisions; those require separate checks.

### Context Consistency And Impact

Use this `Phase Agent Check` to evaluate whether an understood request is consistent with requirements and decisions that remain in effect, identify affected dependencies, and assess the grounds for conclusions about its consequences.

Evaluate:

- **Applicable Baseline:** Which requirements and decisions are confirmed and remain in effect? Distinguish them from unconfirmed agent proposals and assumptions.
- **Revision Boundaries:** Which earlier conditions does the user explicitly replace or withdraw? A difference from an earlier choice is not itself a conflict.
- **Consistency:** Is the request compatible with the remaining requirements, and is it internally consistent?
- **Dependencies And Impact:** Which decisions, assumptions, and earlier conclusions are affected? Do not treat dependent decisions as automatically revised or reconfirmed.
- **Evidence For Consequences:** Do available facts and reasoning support the conclusions about consequences? Distinguish established consequences, conditional conclusions, and unsupported assumptions.

Retain a result for each criterion rather than only an overall pass or fail. Identify any conflicts, affected dependencies, supported consequences, and missing grounds for assessment. An established conflict and consequences that cannot yet be assessed may coexist in the same request.

For example, the confirmed context requires primary data to remain at home and recovery after the complete loss of the home equipment. The user now requests removal of the only planned external backup. The request can be clear while undermining the current basis for recovery: the recovery requirement remains in effect, its planned means of fulfillment is affected, and the earlier recovery conclusion is no longer supported without another independent copy. This does not establish that recovery is impossible; another backup arrangement may exist.

This check records its findings. Selecting the next `Phase Agent Action Proposal` is a separate workflow step.

## Stepwise Handling Of Multiple Intentions

Recognize all intentions together, but work on one current subject at a time. A subject may involve several categories; categories are not workflow steps and do not define a fixed processing order.

1. **Identify the subjects.** Use `Phase Agent Input Classification` to identify every intention and the content it concerns. If there is only one intention, perform the applicable `Phase Agent Check Set` for that subject.
2. **Check relationships and order.** For multiple intentions, use a `Phase Agent Check Set` to assess their relationships, dependencies, and any order specified by the user. A question may concern a requested revision, and confirmation may depend on the answer. Do not impose a category-based order such as confirmations before corrections before questions.
3. **Resolve consequential ambiguity.** If the available context leaves the order or dependency unclear and different interpretations would affect the result, use the next `Phase Agent Action Proposal` to clarify the dependency or agree on the order. Do not silently select an interpretation or record dependent confirmation as settled.
4. **Process the current subject.** Once the order is clear, perform the applicable `Phase Agent Check Set` and respond about the current subject. Follow an explicit user order without asking for it again; do not require an additional confirmation for every subject. Keep related intentions together when separating them would distort their meaning.
5. **Retain the remaining intentions.** Keep outstanding subjects and their understood relationships in conversation context for subsequent continuation. Do not treat them as rejected or completed. Incorporate new input before continuing, preserve unaffected agreements, and honor the skill's completion and stopping rules rather than requiring the user to finish the pending subjects.

### Compound Response Example

> I confirm the proposed topic. But exclude cloud solutions and explain how recovery would work without them.

This expresses **Express A Decision**, **Provide Or Revise Context**, and **Ask A Question**. The confirmation might depend on whether recovery without cloud solutions is feasible. If the available context does not resolve that dependency, the next interaction could be:

> You confirmed the topic, excluded cloud solutions, and asked about recovery. Should we first examine recovery without cloud solutions, then return to confirming the topic?

In contrast, the following input already specifies the order:

> First explain recovery without cloud solutions. After your answer, I will decide whether to confirm the topic.

Proceed with the explanation after the applicable checks. Leave topic confirmation pending; do not ask the user to confirm the processing order again.

## `Phase User Move`

Use the categories above to interpret intentions in a `Phase User Move`. Detailed handling through phase-specific checks and proposals will be defined separately.
