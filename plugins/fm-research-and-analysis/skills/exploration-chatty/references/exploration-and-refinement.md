# `Exploration And Refinement`

Use this reference when investigating the topic and refining understanding in `Exploration And Refinement`. Use the definitions and terminology rules in [the skill's terms](../SKILL.md#terms). Apply this guidance alongside the shared workflow in `SKILL.md`.

Use the [shared question format](../SKILL.md#present-questions) for every question addressed to the user in this phase.

## Phase Logic

- **Validated baseline.** Research within the exact input that passed validation and the [shared immutability rule](../SKILL.md#input-baseline-and-immutability). Conversation context supplies findings and local decisions, not replacement goals or permissions.
- **Initial checks.** Use available findings and the retained baseline without repeating validation merely because the phase starts or resumes. Missing baseline evidence follows the shared recovery rule; do not ask for a new topic and continue as though it were validated.
- **Targeted clarification.** Clarify local decisions or interpretations within the task. If the request changes the input's goals, criteria, or boundaries, explain the new-run requirement instead of adopting revised wording.

### Developing and Revising a Comparison

Apply [Build the Comparison Before Recommending](../SKILL.md#build-the-comparison-before-recommending) when forming the initial comparison or materially revising it. Use Context Consistency And Impact for comparative conclusions: Applicable Baseline identifies the criteria that make alternatives consequential; Consistency assesses candidate compliance under stated conditions; Dependencies And Impact identifies affected recommendations; Evidence For Consequences assesses support for comparative claims and material gaps in the examined alternatives. Reuse applicable findings. This uses the existing checks without adding a mandatory `Phase Agent Check` or asking the user to approve the candidate search.

For example, assume an initial naming comparison covers reserved sequential numbers, assigned namespaces with local counters, and UUIDv7. Locally generated identifiers are within scope, and date plus a random suffix is then identified as a missing family. A suitable correction is:

> The comparison omitted date plus a random suffix. This adds a candidate; it does not record a scheme choice. The visible date and the identifier-generation mechanism are separate properties. Its generation and duplicate-handling procedure need assessment against the same uniqueness criterion used for the other candidates.
>
> My earlier preference for UUIDv7 for local creation needs reassessment alongside this family. Reserved sequential numbers and assigned namespaces remain open. I recommend comparing the two local-generation approaches next because the omitted family could change that recommendation; neither brevity nor a visible date is a mandatory requirement unless the input establishes it.

This is an illustrative reassessment, not a required candidate list or authorization to resume an unselected request. Use actual evidence and candidate statuses; the shared rules govern exclusions, focus, and limited results.

### Focused Analysis Within a Comparison

Apply the shared [return-to-comparison guidance](../SKILL.md#return-to-the-overall-comparison) during candidate analysis in this phase. Use Request Clarity's Subject and Scope findings to distinguish a local configuration choice from scheme selection or exclusion. Use Context Consistency And Impact's Applicable Baseline, Revision Boundaries, Dependencies And Impact, and Evidence For Consequences findings to assess its effect on the overall comparison. Reuse findings that remain valid; this adds no mandatory `Phase Agent Check` or confirmation step.

For example, assume the presented proposal has been accepted under the existing confirmation rules: use four random characters without coordination for `YYYYMMDD-rrrr-topic`, with a previously explained residual collision risk. Sequential numbering, ULID, and UUIDv7 remain open. A suitable return is:

> For `YYYYMMDD-rrrr-topic`, four random characters without coordination are accepted, with the stated residual risk. This configures one candidate; the overall scheme has not been selected.
>
> Sequential numbering, ULID, and UUIDv7 remain open. Their mechanisms and costs have been examined in less depth. The required ordering within a day is still unresolved.
>
> I recommend examining sequential-number reservation next, to compare its coordination cost with independent random generation.

This illustrates an overview and recommendation, not a required response template or automatic authorization to investigate numbering. It assumes numbering investigation is within the current comparison's scope and is not an unselected request. If it was an unselected request, do not re-offer it merely because numbering remains open; follow the existing [selection and order rules](#selection-and-order). An exclusion or deferral of any listed candidate changes the overview accordingly; do not reuse an illustrative open status against the actual decisions.

## Input Classification

Use the following categories for `Phase Agent Input Classification` in `Exploration And Refinement`, for both input on phase entry or resumption and subsequent responses. These are local classification labels; do not assume they apply to other `Skill Phase` contexts.

| Category | Intent | Examples |
|---|---|---|
| **Provide Or Revise Context** | Supply or revise research context within the fixed input boundaries. Requests to change the input's topic, goals, conditions, or requirements require a new run and cannot be adopted here. Facts supplied to support another request are context for that request, not a separate revision intention unless they establish or change the agreed framing. | "This candidate requires coordination." / "Exclude this candidate within the agreed scope." |
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

### Feedback Content

During `Phase Agent Input Classification`, distinguish the following kinds of content within the existing categories. They are content attributes, not additional categories or automatically separate intentions; one passage may contain more than one.

- **Factual correction:** A claim that an agent statement is wrong, such as "This identifier is not unique." Identify the disputed statement and its grounds. Verify the claim and correct an established agent error without requesting confirmation. If verification is unavailable, retain the uncertainty rather than adopting the claim as fact. Correcting a fact does not itself authorize changing a user decision.
- **Evaluation:** A user's assessment, such as "This identifier is too long." Retain it as the user's expressed opinion; do not automatically turn it into a requirement, rejection, or proof of a factual defect. Use Request Clarity to determine whether a materially different next step depends on its intended consequence.
- **Intention to change a decision:** An expressed request to change what is considered or agreed, such as "Exclude this format." Identify whether the target is one format, an entire family of options, or a criterion. Assign the existing category by its subject; do not infer that rejecting one example rejects its family or changes a criterion.

An evaluation may accompany a factual correction or a request for change. Preserve these distinctions without inventing an additional intention for each attribute. Use the feedback-handling rules below to resolve consequential uncertainty and propose a specific interpretation.

When criticism identifies an option under consideration as violating the investigation's goal or a criterion, assess both possible intentions: correcting the assessment and excluding the option from further consideration. They may coexist, but a factual correction alone does not establish either exclusion or an intention to keep the option. Treat these as possible interpretations, not automatically two expressed intentions or classification categories. If the intended inclusion or exclusion is not unambiguous, apply the specific Request Clarity rule and ask the disposition question under [Feedback Handling](#feedback-handling), even if the criticism is entirely factual. Ordinary dislike without a stated or contextually established goal or criterion does not trigger this mandatory question.

## Check Selection

Select the applicable `Phase Agent Check Set` from the checks below. Keep classification, check findings, and admission decisions separate.

- **Request Clarity:** Evaluate every input against the current context and pending proposal. If interpretation remains uncertain, preserve the unresolved criteria; do not use a guessed category to perform the requested action.
- **Context Consistency And Impact:** Include this check when developing or materially revising a comparative recommendation, when feedback disputes an option's compliance with an existing requirement or an agent conclusion, when establishing or revising context, accepting or changing substantive decisions, assessing a phase transition, or answering a question or result request that affects existing requirements, decisions, assumptions, or conclusions. A narrow explanation unrelated to those matters does not require unrelated consistency work.
- **Phase Transition Readiness:** Include this check for the selected request to advance to the next `Skill Phase`, using the current clarity and consistency findings. Do not treat pause, stop, format changes, or action selection as phase transitions.

For restricted mixed input, evaluate what is needed to identify the requests, their relationships, and relevant constraints before offering action selection. Do not solve all unselected requests as part of checking them; the independent-question exception below permits explanatory answers without authorizing the other requests. After selection, evaluate the selected action and its dependencies. Reuse findings that remain applicable; reassess findings affected by new input. The checks record results; use those results under the admission and confirmation rules below.

## Phase Agent Checks

### Request Clarity

Use this `Phase Agent Check` to determine whether the user's request, together with the available context, supports an unambiguous understanding of the expected response or action, its subject, and its scope.

Evaluate:

- **Intent:** Is it clear what the user expects, such as an explanation, revision, confirmation, or another result?
- **Subject:** Is it clear which proposal, requirement, document, statement, or other content the request concerns? Resolve references such as "this option" using the available context.
- **Scope:** Is it clear which parts the request affects and how broadly the requested response or change applies?
- **Relationships:** For compound input, is it clear how the intentions relate? Determine whether confirmation is conditional, a correction replaces an earlier requirement, or a decision depends on an answer. Mark this criterion as not applicable when there are no relationships to evaluate.

Clarification is required when at least two plausible interpretations remain and choosing between them would materially change the next response, action, or recorded decision. A merely conceivable alternative interpretation is not sufficient reason to require clarification.

A negative evaluation alone establishes neither an intention to exclude an option nor the absence of a request for action. Explicit wording such as "Exclude it" or "Do not consider it" expresses an intention to change the considered set; evaluate its subject and scope rather than inferring a broader exclusion.

For criticism that an option violates the investigation's goal or a criterion, evaluate the intention to correct the assessment separately from the intention to exclude the option. If inclusion or exclusion is not unambiguous, record Clarification Required for Intent and any unresolved Subject or Scope, retaining the alternatives of exclusion and continued comparison with the identified deficiency. Do not mark the input Clear solely because the factual criticism is understood or the agent's error has been corrected. If exclusion or retention is already explicitly requested or confirmed, do not reopen that intention; assess any remaining scope or relationship ambiguity and apply the existing admission and confirmation rules.

For other negative evaluations without an explicit action, assess whether plausible interpretations would materially change the next response, action, or recorded decision. If so, record the unresolved intention or scope as Clarification Required. Otherwise, the evaluation alone does not require clarification or confirmation. This check records findings; [Feedback Handling](#feedback-handling) uses them to formulate the question and preserve the current decision.

Record one of these outcomes:

- **Clear:** No material ambiguity remains, or the available context resolves it.
- **Clarification Required:** Material ambiguity remains. Retain the check result, identifying each unresolved criterion from the Evaluate list, the ambiguous content, the plausible interpretations, and why the difference matters.

For example, "Remove the second option" is clear when the immediately preceding discussion contains one relevant numbered list. It requires clarification when several lists remain plausible and the available context does not identify the intended one.

This check evaluates clarity of understanding. It does not establish context completeness, feasibility, or consistency with earlier decisions; those require separate checks.

### Context Consistency And Impact

Use this `Phase Agent Check` to evaluate whether an understood request is consistent with requirements and decisions that remain in effect, identify affected dependencies, and assess the grounds for conclusions about its consequences.

Evaluate:

- **Applicable Baseline:** Which requirements and decisions are confirmed and remain in effect? Distinguish them from unconfirmed agent proposals and assumptions.
- **Revision Boundaries:** Which earlier conditions does the user explicitly replace or withdraw? A difference from an earlier research choice is not itself a conflict. The validated input cannot be replaced or withdrawn within this run; requests affecting it follow the shared new-run rule.
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
- When **Direct The Interaction**, **Express A Decision**, or **Provide Or Revise Context** occurs alongside another category, do not execute the requested substantive actions, adopt proposed revisions, record substantive acceptance, or advance to another `Skill Phase` from that mixed input. The following exception permits only independent explanatory answers.
- For input containing feedback, answer an unambiguous **Ask A Question** intention independently while another part awaits clarification or separate action selection, provided the answer does not depend on that unresolved part, assume the proposed change, violate the user's explicit order, or continue work the user has asked to pause or stop. Answering does not select or authorize any other request. Apply the remaining admission and confirmation requirements to those requests; do not ask the user to select a question already answered.

A mixed request may be clear in meaning and still require separate selection or confirmation under this workflow. Do not report a procedural restriction as a Request Clarity failure.

### Selection And Order

For mixed input requiring separate selection, apply the following steps to the remaining requests after any independent explanatory answer permitted above:

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

This example assumes excluding cloud solutions is a local candidate decision permitted by the input. If it changes an input boundary, explain the new-run requirement instead of proposing adoption.

> Exclude cloud solutions, then move on to the final synthesis.

This contains **Provide Or Revise Context** and **Direct The Interaction**. The order is explicit, but the mixed input requires separate action selection.

A suitable response is:

> You proposed two actions: exclude cloud solutions, then begin the final synthesis. This workflow handles these separately. Unselected actions will not be resumed automatically; please request the transition separately if you want it afterward.
>
> ❓ **Q1 — Current action:** Shall we begin by reviewing the proposed context change?
>
> - **A.** Begin reviewing the proposed context change.
> - **B.** Do not begin that action yet.
> - **C. Custom answer** — Specify another current action or correct the proposed order.
>
> Reply, for example: `Q1: A` or `Q1: C — <your answer>`.

After the user selects the context change, present its proposed wording for confirmation. Do not treat selection of that action as confirmation of the wording.

If the user instead requests the transition, retain the unresolved context issue for assessment. Do not infer that the user withdrew the proposed condition merely by selecting another action.

### Feedback Handling

Use the feedback attributes and check findings to distinguish an error correction from a proposed change to the user's decisions.

1. **Correct established errors.** Verify disputed facts and assess consequences under the existing goal and criteria. Correct an established agent error immediately without asking the user to approve the correction. If an option violates a goal or criterion, state the finding and stop recommending it as satisfying that goal or criterion. If the alleged defect is unverified or disproved, report that accurately. None of these findings is itself the user's decision to exclude the option or relax a criterion.
2. **Ask about exclusion for goal or criterion criticism.** When the user criticizes an option's compliance with the investigation's goal or a criterion and inclusion or exclusion is not unambiguous, you must ask one concrete question: exclude the identified option from further consideration, or retain it for comparison with the identified deficiency recorded? Name the exact option or standalone scheme and the boundaries of exclusion; do not extend rejection of one format to its entire family. Where relevant, state which combinations or other options are outside that boundary. If the alleged deficiency is not established, describe it as an allegation or open issue rather than a confirmed defect. Correcting the factual assessment does not fulfill this clarification requirement. An already explicit exclusion request or confirmation needs no repeated question about intent; an explicit request to retain the option also resolves that intention. Apply the existing admission and confirmation rules to any requested change.
3. **Handle other evaluations proportionately.** Outside goal or criterion criticism, ask a focused clarification question only if plausible interpretations would materially change the next step. Otherwise, reflect the user's opinion in the explanation without additional confirmation. Do not create a mandatory exclusion question for every negative assessment.
4. **Make the question concrete.** Formulate the clarification as a `Phase Agent Action Proposal` identifying the exact subject and scope. For the mandatory disposition question, present exclusion and retention for comparison as alternatives rather than presuming rejection. For other consequential feedback, propose the specific plausible change and ask the user to confirm or correct it. Do not first ask a generic question and then request confirmation of the same unchanged interpretation.
5. **Preserve the current decision until the answer.** Keep exclusion separate from accepted decisions until the user answers unambiguously and applicable admission and confirmation requirements are satisfied. Retain the option's current inclusion or exclusion status in the meantime. This does not suppress a verified defect, justify recommending the option as compliant, or prevent correction of its factual assessment. Do not record exclusion as a user decision merely because the user identified a defect.
6. **Apply the answer precisely.** Update only the confirmed subject and scope. Keeping the option for comparison does not withdraw the criterion or establish compliance. An unqualified answer to the concrete proposal satisfies confirmation for that unchanged content; a correction, qualification, or other independent intention requires reassessment under the existing rules. Do not add an intent-clarification round when exclusion has already been explicitly requested or confirmed.

For example, assume the investigation requires unique identifiers and `YYYYMMDD-topic` uses only the date as its identifier. The user says:

> `20261113-topic` assumes the identifier `20261113`, which is not unique at all.

A suitable response is:

> Correct: a date alone does not ensure uniqueness. The following choice concerns only `YYYYMMDD-topic` as a standalone scheme; it does not affect combinations of a date with another identifier.
>
> ❓ **Q1 — Standalone scheme:** Exclude `YYYYMMDD-topic` from further consideration or keep it for comparison with this deficiency noted?
>
> - **A.** Exclude only the standalone scheme `YYYYMMDD-topic`.
> - **B.** Keep it for comparison with the uniqueness deficiency recorded.
> - **C. Custom answer** — Specify another action, correct the scope, or ask a question.
>
> Reply, for example: `Q1: A` or `Q1: C — <your answer>`.

The factual correction is immediate. Excluding the standalone scheme remains undecided until the answer. Do not broaden this question to all date-based identifiers. If the user instead says "Exclude `YYYYMMDD-topic` as a standalone scheme," apply the existing change-admission and confirmation rules without asking again whether exclusion is intended.

Answer independent questions from the same message in the same response when the category-combination exception applies, alongside the focused disposition question. For example, an independent explanation of UTC need not wait for the exclusion decision. Do not let that answer imply acceptance, rejection, or withdrawal of the criterion. A question whose answer depends on retaining or excluding the option must wait for the relevant clarification; preserve the user's explicit ordering and stopping instructions.

## Explicit Confirmation

For research context within the fixed input boundaries, before adopting newly established or revised context under **Provide Or Revise Context**, present the proposed wording and request explicit confirmation. Until confirmation, distinguish the proposed context from the agreed context.

Before accepting a substantive choice under **Express A Decision**, ensure that the exact proposal being accepted has been presented to the user. If the proposal has not been presented, restate it and request confirmation. A clear acceptance of an already presented proposal is sufficient.

Several changes or decisions within one category may be presented as a single confirmation block when each item is explicit and their joint acceptance is unambiguous.

An unqualified confirmation of the pending proposal completes that confirmation step. Do not request confirmation of the same unchanged content again.

An answer containing a new condition, correction, or substantive request is not an unqualified confirmation. Classify it again and apply the category-combination rules.

For phase transitions, follow [the transition protocol](../SKILL.md#transition-protocol). Confirmation of context wording or a substantive choice is not confirmation of a transition, and confirmation does not override missing entry information or unresolved blocking findings.

Checks record findings. The workflow uses those findings to select the next `Phase Agent Action Proposal`; the checks themselves do not request confirmation or perform actions.

## `Phase User Move`

Use the categories and admission rules above to interpret a `Phase User Move`. Apply the explicit-confirmation requirements before adopting context changes or accepting substantive decisions, and the [phase-transition requirements](../SKILL.md#phase-transitions) before changing phases.

## Diagnostic Output

Only while `Debug Mode` is enabled and `Exploration And Refinement` is active, read [the phase diagnostic instructions](exploration-and-refinement-debug.md). Follow the shared [mode controls and loading rules](../SKILL.md#debug-mode).
