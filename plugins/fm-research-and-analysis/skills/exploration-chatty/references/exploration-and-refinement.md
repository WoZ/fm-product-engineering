# `Exploration And Refinement`

Use this reference when investigating the topic and refining understanding in `Exploration And Refinement`. Use the definitions and terminology rules in [the skill's terms](../SKILL.md#terms). Apply this guidance alongside the shared workflow in `SKILL.md`.

## Phase Logic

- **Topic and available context.** Use the topic, supplied materials, and relevant conversation context.
- **Initial checks.** On entry to or resumption of this phase, the first `Phase Agent Check Set` uses the available input and established context. Do not ask the user to repeat a topic already available in that context. Check whether a topic is present and, when one is present, whether its meaning and the available context are sufficient for the next step.
- **Missing topic.** If no topic can be identified, use that check result to formulate a `Phase Agent Action Proposal` asking for the topic. When a topic is present, use the clarity and context check results to formulate the appropriate next interaction.
- **Targeted clarification.** When establishing the topic and context, ask only about missing information that materially affects the answer or next step.

## Input Classification

Use the following categories for `Phase Agent Input Classification` in `Exploration And Refinement`, for both input on phase entry or resumption and subsequent responses. These are local classification labels; do not assume they apply to other `Skill Phase` contexts.

| Category | Intent | Examples |
|---|---|---|
| **Provide Or Revise Context** | Independently establish or revise the investigation's topic, context, conditions, or requirements. Facts supplied to support another request are context for that request, not a separate revision intention unless they establish or change the agreed framing. | "Let's investigate home storage." / "Exclude cloud solutions." |
| **Express A Decision** | Accept, select, reject, withdraw, or defer a substantive proposal about the investigation. This includes confirmation of presented context wording; interaction controls and phase-transition confirmations belong to Direct The Interaction. | "I choose the second storage option." / "I confirm the proposed context." |
| **Ask A Question** | Request an explanation about the investigation's subject or the skill's behavior. | "What does high availability mean?" / "Why are you asking for confirmation again?" |
| **Request Assistance Or A Result** | Ask for options, help framing the topic, a summary, a document, or a saved result. | "Help me narrow the topic." / "Save the agreed context." |
| **Direct The Interaction** | Control the discussion's format, order, or current action; request or confirm a phase transition; or pause, resume, or stop work. Classify the same control intention only here, even when expressed as a selection or confirmation. | "Start with the explanation." / "I confirm the transition to the final synthesis." / "Let's stop." |

### Classification Rules

Classify independent intentions, not sentences. Several sentences may provide context for one request; one sentence may request several independent results.

- Assign one category to each identified independent intention according to the category definitions, its subject, and the current `Phase Agent Action Proposal`. Do not assign overlapping categories to the same intention.
- Interpret an answer to a pending selection or confirmation according to what that proposal asked the user to decide. Choosing the current action is interaction control; accepting proposed context wording is a substantive decision.
- Distinguish expressed intentions from alternative interpretations. For example, "What about cloud storage?" may be a question or a proposed revision. Retain that uncertainty for Request Clarity rather than treating both interpretations as established intentions.
- Keep supporting facts and conditions with the request they qualify. For example, "I use Proxmox. Explain LXC versus VMs" is an explanation request with context, not automatically two independent requests. "Update the agreed platform from VMware to Proxmox" independently requests a context revision.
- A qualification that changes a proposal is a proposed revision, not acceptance of the unchanged proposal. Preserve any separate question or other independent request alongside it.
- Associate every intention with its subject and scope. Partial confirmation does not accept unrelated proposals. Multiple independent intentions may share one category.
- Classification does not apply revisions, record acceptance, or establish readiness. Describe a clear intention outside the listed categories directly; do not force it into a category or use an uncertain classification to bypass admission requirements.

## Check Selection

Select the applicable `Phase Agent Check Set` from the checks below. Keep classification, check findings, and admission decisions separate.

- **Request Clarity:** Evaluate every input against the current context and pending proposal. If interpretation remains uncertain, preserve the unresolved criteria; do not use a guessed category to perform the requested action.
- **Context Consistency And Impact:** Include this check when establishing or revising context, accepting or changing substantive decisions, assessing a phase transition, or answering a question or result request that affects existing requirements, decisions, assumptions, or conclusions. A narrow explanation unrelated to those matters does not require unrelated consistency work.
- **Phase Transition Readiness:** Include this check for the selected request to advance to the next `Skill Phase`, using the current clarity and consistency findings. Do not treat pause, stop, format changes, or action selection as phase transitions.

For restricted mixed input, evaluate what is needed to identify the requests, their relationships, and relevant constraints before offering action selection. Do not solve all unselected requests as part of checking them. After selection, evaluate the selected action and its dependencies. Reuse findings that remain applicable; reassess findings affected by new input. The checks record results; use those results under the admission and confirmation rules below.

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

### Phase Transition Readiness

Use this `Phase Agent Check` when **Direct The Interaction** expresses a request to move to the next `Skill Phase`, rather than to pause, stop, or change the discussion format. Determine whether the established topic, context, and current results are sufficient to begin that phase under its explicitly defined entry requirements.

Use the current results of Request Clarity to identify the requested transition and Context Consistency And Impact to account for consistency and consequences. Do not duplicate their evaluations within this check.

Evaluate:

- **Required Entry Information:** Are the mandatory inputs for the next phase present? For a transition from `Exploration And Refinement` to `Results Consolidation`, this includes understanding the requested final synthesis and having enough findings, reasoning, and current decisions to produce it. Unresolved choices and evidence limitations must be identified and representable accurately in the result.
- **Blocking Gaps:** Would the next step require a material guess about the user's intentions? Distinguish such gaps from unknown facts that the investigation itself is meant to establish.
- **Available Working Context:** Are the necessary agreements and materials available for the next step? A separately saved document is not required.

Record one of these outcomes when the entry requirements allow the assessment:

- **Ready:** Mandatory entry information is available, and no blocking gaps remain.
- **Not Ready:** Retain the missing information and explain why each gap prevents the next phase from beginning.

For example, a request to consolidate home-storage findings may be ready when the intended synthesis is understood and the available comparison and decisions support it, even if an unresolved technology choice can only be documented as open. If the requested result requires a recommendation but the available findings do not support one, the gap may prevent readiness. A deliberately limited synthesis may remain incomplete; do not invent agreement or research to make it appear final.

Use the entry requirements for `Results Consolidation` in [the phase-transition requirements](../SKILL.md#readiness-requirements). Do not invent additional mandatory inputs.

This check records readiness and gaps. It does not request confirmation or perform the transition.

## Input Admission And Action Selection

Apply these rules after `Phase Agent Input Classification` and the applicable checks.

### Category Combinations

- When the input contains only one category, process it under that category's requirements.
- **Ask A Question** and **Request Assistance Or A Result** may be processed together when their subjects, dependencies, and processing order are clear. Otherwise, clarify the unresolved relationship or order before performing dependent work.
- When **Direct The Interaction**, **Express A Decision**, or **Provide Or Revise Context** occurs alongside another category, do not execute the requested substantive actions, adopt proposed revisions, record substantive acceptance, or advance to another `Skill Phase` from that mixed input.

A mixed request may be clear in meaning and still require separate selection or confirmation under this workflow. Do not report a procedural restriction as a Request Clarity failure.

### Selection And Order

For mixed input requiring separate selection:

1. Show the independent requests and their recognized categories. Use plain-language action descriptions alongside the category labels.
2. State that the workflow requires selecting the current action separately.
3. If the user specified an order, restate it and ask whether to begin with its first action. Do not ask the user to reconstruct an already explicit order.
4. Otherwise, ask the user to select one action to process now.
5. Explain that unselected requests will not be scheduled or resumed automatically. The user must explicitly request them again.
6. Interpret the user's selection as a response to this pending `Phase Agent Action Proposal`, not as a new substantive decision requiring another action-selection round.

Selecting the current action or confirming an order does not authorize automatic execution of later actions, adoption of proposed context changes, or a phase transition.

Do not maintain a task queue from unselected requests or prompt the user to return to them after the selected action. Preserve relevant facts, existing agreements, and unresolved conditions without treating them as queued tasks. Withdrawing a request does not withdraw a requirement unless the user explicitly does so.

While resolving a request to pause or stop, do not initiate additional investigation or continue the potentially affected work. Honor the skill's completion and stopping rules.

### Mixed Input Example

> Exclude cloud solutions, then move on to the final synthesis.

This contains **Provide Or Revise Context** and **Direct The Interaction**. The order is explicit, but the mixed input requires separate action selection.

A suitable response is:

> You proposed two actions: exclude cloud solutions, then begin the final synthesis. This workflow handles these separately. Shall we begin by reviewing the proposed context change? Unselected actions will not be resumed automatically; please request the transition separately if you want it afterward.

After the user selects the context change, present its proposed wording for confirmation. Do not treat selection of that action as confirmation of the wording.

If the user instead requests the transition, retain the unresolved context issue for assessment. Do not infer that the user withdrew the proposed condition merely by selecting another action.

## Explicit Confirmation

Before adopting newly established or revised context under **Provide Or Revise Context**, present the proposed wording and request explicit confirmation. Until confirmation, distinguish the proposed context from the agreed context.

Before accepting a substantive choice under **Express A Decision**, ensure that the exact proposal being accepted has been presented to the user. If the proposal has not been presented, restate it and request confirmation. A clear acceptance of an already presented proposal is sufficient.

Several changes or decisions within one category may be presented as a single confirmation block when each item is explicit and their joint acceptance is unambiguous.

An unqualified confirmation of the pending proposal completes that confirmation step. Do not request confirmation of the same unchanged content again.

An answer containing a new condition, correction, or substantive request is not an unqualified confirmation. Classify it again and apply the category-combination rules.

For phase transitions, follow [the transition protocol](../SKILL.md#transition-protocol). Confirmation of context wording or a substantive choice is not confirmation of a transition, and confirmation does not override missing entry information or unresolved blocking findings.

Checks record findings. The workflow uses those findings to select the next `Phase Agent Action Proposal`; the checks themselves do not request confirmation or perform actions.

## `Phase User Move`

Use the categories and admission rules above to interpret a `Phase User Move`. Apply the explicit-confirmation requirements before adopting context changes or accepting substantive decisions, and the [phase-transition requirements](../SKILL.md#phase-transitions) before changing phases.
