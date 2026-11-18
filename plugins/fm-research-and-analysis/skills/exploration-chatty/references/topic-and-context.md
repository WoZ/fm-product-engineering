# `Topic And Context`

Use this reference to receive and validate input. Apply the [shared workflow and terminology](../SKILL.md), [input immutability](../SKILL.md#input-baseline-and-immutability), and [question format](../SKILL.md#present-questions). This phase does not clarify the research task through dialogue or begin research.

## Read and Check the Input

1. Read the user-identified file or accept complete Markdown supplied in chat. If missing, ask for the file path or full Markdown; do not search for an unspecified input. If several sources are plausible, clarify which version to check. Do not fill missing document content from conversation history.
2. Use the shared [input template](../../../references/exploration/input-template.md), [readiness criteria](../../../references/exploration/input-readiness-criterias.md), and [validation result format](../../../references/exploration/validation-result-template.md) through [exploration-input-validation](../../exploration-input-validation/SKILL.md). They own format and document-readiness requirements; do not add a research plan or a brief questionnaire as prerequisites.
3. Always follow [isolated validation](../../../references/exploration/isolated-validation.md), even in a session that contains only the input. Start a fresh subagent without parent history for each attempt; never resume the previous validator. Supply the exact Markdown as data, the resolved installed validator path, and the request to return its prescribed report. Do not send prior reports, expected answers, dialogue summaries, or extra task evidence. Wait for the final report. Do not validate directly in the main conversation.
4. Accept a report only for the exact submitted version. If that version changes before the report is used, submit the new version to a fresh validator. A report without a prescribed PASS or FAIL status is not usable. A FAIL report must also contain actionable problem and needed-correction details. Input that cannot be read and unavailable validation resources are handled under the validator's failure rules; do not invent a document verdict when no validation ran.
5. On `FAIL`, explicitly state that validation failed and relay the report's problems and needed corrections in the user's language. Translate explanations faithfully while retaining exact identifiers. Use only the report as evidence; do not resolve open choices from earlier messages or suggest unsupported values. Stay in `Topic And Context` without offering a transition. Wait for complete corrected Markdown or an explicit request to reread the corrected file, then repeat isolated validation. The agent never edits or rewrites input.
6. On `PASS`, retain the exact validated version, source, and report under the shared baseline rule. Present the transition to `Exploration And Refinement` under the [transition protocol](../SKILL.md#transition-protocol). Do not start research until the user explicitly confirms; a request accompanying the submitted input is not confirmation of a subsequently presented transition.

If a fresh subagent cannot start or returns no usable report, state the actual technical limitation and apply the shared new-chat handoff. Show the exact pending Markdown for transfer, request validation in a new chat, and wait for the report plus confirmation that this exact version was checked. Do not substitute an old report or a parent-context check. Every subsequent check normally uses a new subagent; the handoff remains available when isolated execution is unavailable or fails.

Questions about the report, input format, or workflow may be answered without conducting the research or reconstructing input. A user request to stop ends work without validation, transition, or an extra procedural question.

## Input Classification

Use the following categories for `Phase Agent Input Classification` in `Topic And Context`, for both initial input and subsequent responses. These are local classification labels; do not assume they apply to other `Skill Phase` contexts.

| Category | Intent | Examples |
|---|---|---|
| **Provide Or Revise Context** | Supply complete input Markdown or a replacement version before PASS. A request to change a validated task is classified but cannot be adopted in this run. | "Here is the complete corrected Markdown." |
| **Express A Decision** | Accept, select, reject, withdraw, or defer a substantive proposal about the investigation. This does not approve edits to the input; interaction controls and phase-transition confirmations belong to Direct The Interaction. | "I accept that recommendation." (Research choices wait for the research phase.) |
| **Ask A Question** | Request an explanation of the input, validation report, or skill behavior; substantive research waits for the confirmed transition. | "Why did validation fail?" / "Why is transition confirmation required?" |
| **Request Assistance Or A Result** | Request assistance or an output; research and input rewriting remain outside this phase. | "Explain the validation report." / "Rewrite my input." (Do not rewrite it.) |
| **Direct The Interaction** | Control the discussion's format, order, or current action; request or confirm a phase transition; or pause, resume, or stop work. Classify the same control intention only here, even when expressed as a selection or confirmation. | "Start with the explanation." / "I confirm the transition to research." / "Let's stop." |

### Classification Rules

Classify independent intentions, not sentences. Several sentences may provide context for one request; one sentence may request several independent results.

- Assign one category to each identified independent intention according to the category definitions, its subject, and the current `Phase Agent Action Proposal`. Do not assign overlapping categories to the same intention.
- Interpret an answer to a pending selection or confirmation according to what that proposal asked the user to decide. Choosing the current action is interaction control; accepting a substantive proposal is a substantive decision, subject to the fixed-input boundary.
- Distinguish expressed intentions from alternative interpretations. For example, "What about cloud storage?" may be a question or a proposed revision. Retain that uncertainty for Request Clarity rather than treating both interpretations as established intentions.
- Keep supporting facts and conditions with the request they qualify. For example, "I use Proxmox. Explain LXC versus VMs" is an explanation request with context, not automatically two independent requests. "Update the agreed platform from VMware to Proxmox" independently requests a context revision; after PASS it requires a new run.
- A qualification that changes a proposal is a proposed revision, not acceptance of the unchanged proposal. Preserve any separate question or other independent request alongside it.
- Associate every intention with its subject and scope. Partial confirmation does not accept unrelated proposals. Multiple independent intentions may share one category.
- Classification does not apply revisions, record acceptance, or establish readiness. Describe a clear intention outside the listed categories directly; do not force it into a category or use an uncertain classification to bypass admission requirements.

## Check Selection and Results

Select the applicable `Phase Agent Check Set` without duplicating document validation:

- **Request Clarity:** Evaluate Intent (requested action), Subject (source/version or proposal), Scope (affected content), and Relationships (dependencies between intentions; Not Applicable when absent). Record Clear or Clarification Required, retaining the unresolved criteria and why they matter. Do not use this check to repair or approve the research task from chat context.
- **Context Consistency And Impact:** When a request affects the baseline, decisions, or transition, record findings for Applicable Baseline, Revision Boundaries, Consistency, Dependencies And Impact, and Evidence For Consequences. Distinguish a user-supplied replacement before PASS from a forbidden change after PASS. No confirmation can waive the immutable-input rule.
- **Phase Transition Readiness:** When assessing advancement, use Required Entry Information (the exact validated Markdown and its usable PASS report), Blocking Gaps (failed or unavailable validation), and Available Working Context (the baseline and report are retained). Record Ready or Not Ready with the missing prerequisite. Reuse the external verdict; do not rerun its ten criteria yourself. This check does not request or perform the transition.

The external validation report is separate from these `Phase Agent Check` results. Selecting an action, accepting wording, or obtaining a clear user reply does not produce PASS.

## Input Admission And Action Selection

Apply these rules after `Phase Agent Input Classification` and the applicable checks.

### Category Combinations

- When the input contains only one category, process it under that category's requirements.
- **Ask A Question** and **Request Assistance Or A Result** may be processed together when their subjects, dependencies, and processing order are clear. Otherwise, clarify the unresolved relationship or order before performing dependent work.
- When **Direct The Interaction**, **Express A Decision**, or **Provide Or Revise Context** occurs alongside another category, do not execute the requested substantive actions, adopt proposed revisions, record substantive acceptance, or advance to another `Skill Phase` from that mixed input. The following exception permits only independent explanatory answers.
- For input containing feedback, an unambiguous **Ask A Question** intention may be answered independently while another part awaits clarification or separate action selection, provided the answer does not depend on that unresolved part, assume the proposed change, violate the user's explicit order, or continue work the user has asked to pause or stop. Answering does not select or authorize any other request. Apply the remaining admission and confirmation requirements to those requests; do not ask the user to select a question already answered.

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

### Explicit Confirmation

Before accepting a substantive choice under **Express A Decision**, ensure that the exact proposal being accepted has been presented to the user. If the proposal has not been presented, restate it and request confirmation. A clear acceptance of an already presented proposal is sufficient.

These confirmation rules do not permit rewriting input or adopting task changes. PASS needs no extra content-confirmation ceremony; the phase transition still requires its own confirmation.

An unqualified confirmation of the pending proposal completes that confirmation step. Do not request confirmation of the same unchanged content again.

An answer containing a new condition, correction, or substantive request is not an unqualified confirmation. Classify it again and apply the category-combination rules.

For phase transitions, follow [the transition protocol](../SKILL.md#transition-protocol). Confirmation of context wording or a substantive choice is not confirmation of a transition, and confirmation does not override missing entry information or unresolved blocking findings.

Checks record findings. The workflow uses those findings to select the next `Phase Agent Action Proposal`; the checks themselves do not request confirmation or perform actions.

## `Phase User Move`

Apply the classification and admission rules above to supplied input, requests to reread, report questions, transition confirmations, and stopping. Revisions after PASS follow the new-run boundary, regardless of category or confirmation.

## Diagnostic Output

Only while `Debug Mode` is enabled and `Topic And Context` is active, read [the phase diagnostic instructions](topic-and-context-debug.md).
