# `Exploration And Refinement`

Use this reference when investigating the topic and refining understanding in `Exploration And Refinement`. Use the definitions and terminology rules in [the skill's terms](../SKILL.md#terms). Apply this guidance alongside the shared workflow in `SKILL.md`.

Use the [shared question format](../SKILL.md#present-questions) for every question addressed to the user in this phase.

## Phase Logic

- **Validated baseline.** Research within the exact input that passed validation and the [shared immutability rule](../SKILL.md#input-baseline-and-immutability). Conversation context supplies findings and local decisions, not replacement goals or permissions.
- **Initial checks.** Use available findings and the retained baseline without repeating validation merely because the phase starts or resumes. Missing baseline evidence follows the shared recovery rule; do not ask for a new topic and continue as though it were validated.
- **Targeted clarification.** Clarify local decisions or interpretations within the task. If the request changes the input's goals, criteria, or boundaries, explain the new-run requirement instead of adopting revised wording.

### Discussion Path and Navigation

Start every ordinary response in this phase with one separate inline-code path showing the current topic's ancestry, for example: `"A1: Directory naming schemes" -> "A2: Shared sequential number" -> "A3: The Git repository"`. The path is visible with `Debug Mode` Off as well as On. It shows the current focus, not the sequence of past visits. It does not represent a `Skill Phase` transition or require transition confirmation.

Maintain the tree, current node, next unused identifier, and each comparison's complete option list with stable local numbers and its owning node in conversation context. A list belongs to the node where its options are compared; a child opened from one option does not inherit that list. For each node, retain its identifier, exact title, parent, related option when applicable, material findings, and unresolved questions. Candidate statuses and decisions remain governed by the [shared decision boundaries](../SKILL.md#candidate-state-and-decision-boundaries). Do not create a tracking file or require a diagram in each response.

#### Titles and Identifiers

- The first research response establishes A1 as the root, with a descriptive title in the user's language. Do not label it Root. Allocate A2, A3, and subsequent identifiers consecutively as new topics are opened, whether deeper or in a sibling branch.
- When first presenting options that can become discussion topics, give each a distinct title of two to four words, with explanation separate from the title. This length requirement applies to initial title generation, not to the full option text or later path rendering. Preserve exact technical identifiers within titles when needed.
- Opening a previously listed option must reuse its exact title. Resolve a user's paraphrase to that option; do not generate a synonym as the node title. A topic not previously listed receives its own two-to-four-word title when opened.
- Merely listing an option does not allocate a node identifier. Revisiting an existing topic reuses its identifier and title. Additional explanation of the same subject does not create a node. Topic identifiers A1 and onward are independent of question identifiers Q1 and onward and answer letters.
- Preserve the tree and counter on resumption or a confirmed return from `Results Consolidation` when available in context. A new exploration starts again at A1. If a requested identifier cannot be resolved from available context, use Request Clarity to recover the reference; do not invent its meaning or silently reuse it for another topic.

#### Local Option Numbers and Presentation

Every option must have a local number immediately beside its title from the first presentation, even before it has a discussion node. Each separate comparison list starts at 1 and continues with 2, 3, and so on. Do not prefix numbers with a parent's number: a nested list starts again at 1, not 2.1. Retain each option's number on clarification, rejection, reordering, redisplay, and return. Append new options using the next unused number in that list; do not renumber survivors or reuse an excluded option's number.

Local numbers are stable labels within one comparison, not global node identifiers or question-answer letters. Resolve "option 3" against the current comparison when unambiguous. If multiple lists remain plausible, use Request Clarity to identify the intended list before acting. A bare number does not select an option from an unrelated list. Opening the option creates or revisits its A-identifier under the existing rules; its title and local number remain unchanged.

Present each option as a separate text block. Its first line is a bold paragraph containing the literal local number, exact title, and current status, followed by its own A-identifier in parentheses if opened. Put explanatory paragraphs below it and a horizontal rule (`---`, with blank lines around it) between option blocks. Do not use Markdown headings, tables, blockquotes, or automatic ordered-list numbering to present the options. The number must be part of the visible title label regardless of layout. This requirement concerns comparison options, not the shared Q-numbered question format, diagnostic blockquotes, or unrelated diagrams and tables.

Illustrative Markdown source for two blocks within an existing list:

```markdown
**2. Last number file — rejected (A4)**

**How it works.** A request proposes increasing the shared counter.

**Trade-off.** Issuance needs a reliable way to associate an accepted increase with one request.

**Why rejected.** The required issuance check was considered too complex.

---

**3. Per-number reservation file — under consideration (A5)**

**How it works.** Each number has its own reservation record.

**Open question.** The record's acceptance procedure remains to be assessed.
```

Localize labels, statuses, and explanatory prose to the user's language. Select explanatory fields for the content, such as How it works, Trade-off, Why rejected, or Open questions; do not require empty or irrelevant fields. Keep material explanations when updating a block instead of replacing them with a status alone. The local number and A-reference are metadata, not part of the two-to-four-word title or of its exact reuse in the path. These illustrative blocks do not authorize rejection or establish facts for another investigation.

#### Moving Between Topics

Resolve navigation by identifier, exact title, clear paraphrase, or relative direction such as "one level up" or "two levels up." A return goes to the existing ancestor; a sibling discussion uses the same parent. At A1, an upward request remains at A1 rather than creating an artificial parent. A materially ambiguous destination requires clarification under Request Clarity, without a guessed move.

After rejection of the current leaf has been accepted under the existing admission and confirmation rules, move the response's path to its immediate parent and report the scoped rejection there. This is an automatic presentation consequence, not a second independent user intention or a new confirmation step. A proposed or ambiguous rejection does not collapse the path. A clarification that leaves a decision open keeps the topic open; answering an explanatory question alone does not close it. An explicit return changes focus without closing the topic being left.

A return to an excluded topic for explanation does not restore active consideration. Navigation alone does not choose a candidate, accept a configuration, exclude siblings, or authorize unselected requests. Keep the current branch while answering its questions; a substantive result or recap requirement does not itself move discussion to an ancestor. Honor stopping immediately, without an extra list or navigation procedure.

#### Complete Lists and Node References

Apply the [mandatory recap rule](../SKILL.md#when-and-how-to-return) only to lists owned by the current node. After clarification or rejection, repeat every option in that node's existing comparison with its current status, including excluded and deferred options. Keep exclusion reasons visible. If it has no options yet, give the answer without an option list. Do not borrow ancestor lists or generate alternatives merely to fill a recap. A sequence of explanatory steps or mention of a possible mechanism is not automatically a list of choices. For noncandidate discussion questions presented as options, use an appropriate open or resolved status rather than inventing candidate acceptance.

On descent, preserve the parent's list in context and show only the child's own options if any are actually proposed. On return, display the complete list owned by the destination node if it has one. After accepted rejection of the current leaf, the parent becomes current under the existing collapse rule, so show its list with the rejected option and reason. Explain a nested rejection within the parent's block without marking the parent excluded. A question comparing siblings is discussed at their shared comparison level. Several triggers affecting the same current-node list in one response need only one complete recap. Retain all other comparisons and their statuses for later return without displaying them in the current branch.

For each option already opened as a node, append its own identifier in parentheses, for example `1. Shared sequential number — under consideration (A2)` or `2. Last number file — rejected (A4)`. Do not substitute the identifier of its most recent descendant. Unvisited options still have local numbers but no node reference. Preserve the reference after rejection, an unresolved clarification, or departure from the branch. Use the [numbered text-block format](#local-option-numbers-and-presentation) for every option in the complete list.

#### Preserve Node Content on Return

Retain each visited node's latest complete substantive presentation in conversation context, separately from its response path, interaction questions, and diagnostic output. This includes the introduction, option descriptions, examples, limitations, links, conclusion, and recommendation, not just titles and statuses. Preserve its wording, Markdown, and block order. Retain the current presentation rather than concatenating the discussion history; an additional focused answer does not replace an existing complete comparison with a shortened summary. No tracking file is required.

On a return without relevant new findings or decisions, you must reproduce that presentation verbatim. Navigation alone does not authorize summarizing, paraphrasing, rearranging, dropping qualifications or links, or rebuilding the comparison. This applies to nodes without option lists as well. Reuse retained evidence rather than repeating research or tool actions merely to redisplay it; apply the existing checks to the navigation request as needed. Restored descriptions of earlier work do not mean that work was performed again.

When new facts, an established error correction, a confirmed decision, or an explicit request to rewrite affects the node, update only the affected passages and keep the rest verbatim. Briefly identify what changed and why outside the preserved body, then retain the updated presentation for subsequent returns. Update statuses and own-node references under the existing rules without rewriting unaffected explanations. Check for relevant changes established in other branches before restoring the body; content preservation must not restore an obsolete claim or bypass admission and confirmation requirements. A rejected option remains visible with its reason rather than disappearing from the list.

This preservation rule also applies while revising the current node, without leaving and returning. For a revision admitted under the existing action-selection rules, take the latest complete presentation, make the necessary corrections, and display the entire revised substantive body in the same response. This includes nodes containing a mechanism explanation without a comparison list. A change summary, corrected fragment, list of accepted decisions, or reference to earlier text is not a substitute. Preserve unaffected sections, wording, examples, links, and block order. Before sending, compare section coverage with the prior complete presentation; remove content only when the revision itself or an explicit user request warrants removal. This presentation review adds no `Phase Agent Check`.

When confirmation is required, label the full proposed revision as pending and identify its proposed changes separately from accepted content, then ask the existing confirmation question after the body. Do not record proposed content as accepted. If another admitted correction arrives before confirmation, apply it to the latest complete proposed revision, retaining earlier proposed corrections and their pending status. After valid confirmation, display the complete accepted body and retain it for later revisions and returns; a short acknowledgment or decision list does not replace it. Do not ask for confirmation of the same unchanged proposal again. This does not authorize unselected requests or changes to the fixed input.

A simple explanatory question that does not revise the node's content does not require repeating its full narrative; the mandatory current-node option-list rules still apply. Offer the [full-response choice](#full-response-after-explanations) when applicable instead of automatically repeating the narrative. Preserve explicit requests for shorter or bounded output, stopping instructions, and diagnostic-control redisplay. These exceptions do not make an ordinary clarification that changes the content permission to abbreviate its revised presentation.

Use the actual response path and handle interaction questions separately after the substantive body. Preserve a still-pending question's identifier when applicable, never reopen a resolved question merely because it accompanied an earlier presentation, and apply [Continuation Question](#continuation-question) when required. Diagnostic controls continue to follow their own [whole-message redisplay rule](../SKILL.md#redisplay-after-controls).

If the exact presentation is unavailable in context, explicitly state that it cannot be restored verbatim. Do not silently reconstruct it from a summary or present a reconstruction as the original. Recover the missing text when needed instead of inventing wording or prior findings.

Illustrative verification scenarios:

| Scenario | Expected behavior |
|---|---|
| A3 presents five Git reservation implementations; the user visits A1 and returns to A3 without new findings or decisions | Restore A3's full body verbatim, including the journal's duplicate-number warning, examples, links, and recommendation. Handle the current question separately. |
| Return to a node containing only an explanation | Restore that explanation verbatim without importing an ancestor's options. |
| A scoped rejection is confirmed | Update the affected status and rejection reason; preserve unrelated descriptions and apply the existing parent-return rule. |
| A finding in another branch invalidates a claim in A3 | Correct the dependent passage, identify the change, and preserve unaffected text. Do not replay the stale claim. |
| The agent establishes an error or the user explicitly asks for a shorter presentation | Correct or rewrite the affected content as requested; retain the resulting presentation for later returns. |
| A prior question is resolved and Extended diagnostics are enabled | Do not reopen it. Present any currently required question separately and report restoration rather than renewed research in existing diagnostic fields. |
| Only a summary of the old text remains available | Disclose that verbatim restoration is unavailable; do not claim that reconstructed wording is the original. |

Illustrative revision sequence within A4, "Shared request log," whose complete body explains `reservations.tsv`, an example record, issuance steps, concurrent requests, network-failure recovery, uniqueness conditions, and trade-offs:

| Event | Expected presentation |
|---|---|
| The user explains that the topic may be unknown when reserving a number | Show the full proposed body with the topic no longer required for issuance, a corrected example record, and directory creation delayed until a working topic exists. Preserve the technical request identifier, concurrency procedure, recovery explanation, uniqueness conditions, and other unaffected material. Label the proposal as pending if confirmation is required. |
| Before confirmation, the user requests `0043-retry-strategy` instead of `0043--retry-strategy` | Show the full proposed body with consistent naming examples and separator explanations. Keep the earlier topic correction and distinguish both proposed changes from accepted decisions. |
| The user confirms the presented combined proposal | Show the full accepted body, not only the decisions about topic timing and the separator. Preserve unchanged sections verbatim without another confirmation round. |
| The user visits A3 and returns to A4 without further relevant changes | Restore the complete accepted A4 body verbatim with both corrections; do not replace it with two summary paragraphs or import A3's list. |
| The user asks a short question without changing the content | Answer it directly; the full narrative is not mandatory. Preserve any applicable current-node list requirement. |
| The user explicitly asks for a shorter version or stops | Honor that request instead of forcing the full presentation or an extra question. |
| Extended diagnostics are enabled during revision or acceptance | Distinguish proposed and accepted changes and report whether the complete body was displayed, using only existing fields and actual actions. |

#### Continuation Question

During an ongoing discussion, after answering an explanatory question or updating a comparison to reflect exclusions, you must end the ordinary response with a continuation question when the user has not specified the next action and no other necessary question is being presented. A recommendation or option list alone does not fulfill this requirement. Answer the user's question and show any required current-node list first. This also applies to a brief explanation in a node without its own options; do not append an ancestor's list to accompany the question.

Use the [shared question format](../SKILL.md#present-questions), its Q-identifiers, and these choices in order, omitting inapplicable choices:

1. Show the current node's full response incorporating the discussed explanations, naming its actual identifier and exact title, when the [full-response choice](#full-response-after-explanations) applies.
2. Return to the immediate parent, naming its actual identifier and exact title.
3. Return to A1, naming its exact title.
4. **Custom answer** — Invite a question, clarification, correction, or instruction for the next step within the skill's existing boundaries.

If the parent is A1, combine the two destinations into one choice. At A1, omit upward navigation: offer the full-response choice followed by Custom answer when applicable; otherwise use the shared free-response format with a Custom answer prompt and reply example. Calculate destinations from the actual response path, including any parent return after an accepted leaf rejection. Do not allocate a topic identifier merely to offer navigation. Follow the existing Q-identifier rules when introducing a changed menu; do not silently change the meaning of an already presented answer letter.

A necessary clarification, confirmation, or action-selection question replaces this continuation question; do not add a second navigation question or navigation choices to that substantive question. Follow an already specified next action under the existing admission rules instead of asking the user to choose it again. Do not add this question after an explicit completion or stop, a requested bounded final result, a progress-only message, or a diagnostic control-only acknowledgment and redisplay. Answering an explanatory question during continuing exploration is not, by itself, such a completion.

Offering navigation leaves the current node and all candidate statuses unchanged. A navigation selection changes focus under [Moving Between Topics](#moving-between-topics) and displays the destination's own list if present. It neither chooses a candidate nor changes `Skill Phase`. Interpret custom input under the existing classification, admission, and confirmation rules; do not treat the menu as permission to bypass them or resume unselected requests. When `Debug Mode` is enabled, present the question before diagnostics and reference its actual Q-identifier in the existing Extended `Phase Agent Action Proposal` field, without new fields or checks.

##### Full Response After Explanations

After a short explanatory answer, you must offer the full-response choice first in the continuation question when the current node's complete presentation is available and discussed explanations have not yet been incorporated into a full displayed response. Retain those answered explanations in conversation context alongside the complete presentation. This applies to explanations of an existing mechanism that do not change its conditions or conclusions; it does not defer the mandatory full-body output for a substantive revision. Offer this choice only within an otherwise appropriate continuation question, not alongside a necessary clarification or confirmation question or after stopping, a bounded final result, or diagnostic controls alone.

When selected, use the latest complete node presentation and integrate relevant answers and explanations from the discussion into one self-contained full response. Preserve unaffected text verbatim rather than replacing the body with a summary or appending a question-and-answer transcript. Preserve accepted decisions and the pending status of proposals. Clarifying a mechanism does not select it, and requesting this presentation is not acceptance of a substantive proposal. Do not execute unselected requests, repeat research, or ask for an extra confirmation merely to show the text. Stay in the same node and `Skill Phase`, without allocating an A-identifier. Retain the resulting full presentation for later revisions and returns. If the exact prior text is unavailable, apply the existing disclosure and recovery rule rather than claiming faithful restoration.

Do not offer the same full-response choice immediately after displaying the requested full body or a mandatory full revision. Offer it again only after further explanatory answers remain outside the full displayed presentation. Other continuation choices remain governed by the rules above.

Illustrative continuation after a short explanation in `"A1: Directory naming schemes" -> "A2: Shared sequential number" -> "A3: Git-based reservation" -> "A5: Last number file"`; use the actual next Q-identifier and the user's language:

❓ **Q11 — Discussion continuation:** What would you like to do next?

- **A.** Show the full A5 response, "Last number file," incorporating the discussed explanations.
- **B.** Return to A3, "Git-based reservation."
- **C.** Return to A1, "Directory naming schemes."
- **D. Custom answer** — Ask a question or specify the next step.

Reply, for example: `Q11: A` or `Q11: D — <your answer>`.

In this example, explaining `request_id` can remain a short answer. Selecting A then incorporates its origin and purpose and the distinction from a commit hash into the full A5 body. It does not choose `request_id` over commit hashes or imply that either mechanism was newly tested.

##### Continuation Examples and Scenarios

Illustrative ending after presenting Git reservation implementations in `"A1: Directory naming schemes" -> "A2: Shared sequential number" -> "A3: Git-based reservation"`; use the actual titles, next question identifier, and user's language:

❓ **Q5 — Discussion continuation:** What would you like to do next?

- **A.** Return to A2, "Shared sequential number."
- **B.** Return to A1, "Directory naming schemes."
- **C. Custom answer** — Ask about the current options, clarify or correct something, or specify the next step.

Reply, for example: `Q5: A` or `Q5: C — <your answer>`.

Illustrative verification scenarios:

- After presenting implementations in A3, offer A2, A1, and custom input. Merely offering these destinations keeps the path in A3.
- After a short explanation in A3 without its own options, offer the full-response choice first when applicable, then the destinations, without printing A2's or A1's list.
- After an accepted rejection collapses a leaf to A3, show A3's updated complete list and calculate continuation destinations from A3. If exclusion still needs clarification or confirmation, ask that question instead.
- In A2, offer one return to A1 and custom input, preceded by the full-response choice when applicable. At A1, offer that choice and custom input when applicable, otherwise only the free-response prompt; do not invent a parent.
- After several explanatory answers, selecting full output integrates all relevant answered explanations into the full body, preserving unaffected sections and decision statuses. Do not execute unselected requests.
- After the requested full output, omit the repeat choice until further explanations have accumulated. A mandatory full revision is still displayed immediately rather than offered as optional.
- When the user specifies the next action, stops, requests a bounded final result, or changes only diagnostics, do not add a new continuation question. A diagnostic redisplay preserves any previous question without reopening it.
- With Extended diagnostics, reference the continuation question actually shown; do not claim that a proposed return or a new check has occurred.

#### Illustrative Navigation Sequence

This condensed sequence illustrates discussion state, not technical guarantees or required research choices. The complete lists are:

- **S — Schemes:** 1. Shared sequential number; 2. Prefix and local counter; 3. Date and random suffix; 4. UUID naming scheme.
- **M — Issuance methods:** 1. Issue tracking system; 2. The Git repository; 3. Designated number issuer.
- **R — Git implementations:** 1. Shared number list; 2. Last number file; 3. Per-number reservation file; 4. Directory as issuance record.
- **P — Date-scheme questions:** 1. Purpose of date; 2. Random suffix length; 3. Handling duplicate identifiers.

All candidate options initially remain under consideration; P questions are open. S, M, R, and P abbreviate full lists only in this example: actual responses must print the numbered option blocks and statuses, not these abbreviations. Titles are reused exactly in the path. A path column lists identifiers for compactness; ordinary responses include their titles. The following table documents a scenario, not the presentation of comparison options to the user. At step 5, R retains labels 1, 2, 3, and 4 after rejection of option 2; at step 11, S still starts at 1. "Option 3" within R targets Per-number reservation file (A5 after opening), while "Return to A5" identifies that node across comparisons.

| Step | User request or event | Response path | Required list or state |
|---|---|---|---|
| 1 | Initial comparison after the confirmed research transition | A1: Directory naming schemes | Show S; no scheme selected. |
| 2 | Ask whether the shared number needs a separate service; the answer proposes issuance methods | A1 → A2: Shared sequential number | Show M only. Retain S in A1, linking its first scheme to A2. |
| 3 | "Explain issuance through Git"; the answer proposes implementations | A1 → A2 → A3: The Git repository | Show R only. Retain M in A2, linking Git to A3 without renaming it. |
| 4 | Explain the last-number approach | A1 → A2 → A3 → A4: Last number file | Answer without a list: A4 has no own options. Retain R in A3, with option 2 linked to A4. No decision yet. |
| 5 | Explicitly reject only the last-number option; admission and confirmation requirements are satisfied | A1 → A2 → A3 | Repeat all of R; its second option is rejected (A4), with the stated reason. Other options remain under consideration. |
| 6 | Discuss a separate reservation file | A1 → A2 → A3 → A5: Per-number reservation file | Answer without a list: A5 has no own options. Retain R in A3, including rejected A4 and the third option's A5 reference. |
| 7 | "One level up" | A1 → A2 → A3 | Show all of R with unchanged statuses and references. A5 remains open. |
| 8 | Compare the separate file with the directory record | A1 → A2 → A3 | Answer, then repeat R. Do not create a node for a sibling comparison. |
| 9 | "Return to A5" | A1 → A2 → A3 → A5 | Reuse A5; no list because A5 has no own options. No new identifier. |
| 10 | "Two levels up" | A1 → A2 | Show M; Git is under consideration (A3), with the nested rejection identified. |
| 11 | "Return to A1" | A1 | Show S; the shared-number scheme references A2, not A3 or A5. |
| 12 | Discuss the date with a random component; the answer proposes discussion questions | A1 → A6: Date and random suffix | Show P only. Retain S in A1, linking its third scheme to A6. |
| 13 | Explain suffix length without choosing a value | A1 → A6 → A7: Random suffix length | Answer without a list: A7 has no own options. Retain P in A6; length remains open (A7). |
| 14 | Clarify how the alphabet affects length | A1 → A6 → A7 | Answer without P or S; keep A7 and do not record a value choice. |

For the no-options case, suppose A1 has shown four naming schemes and the user asks what "shared registry" means for its first option. The response opens A2 and explains the term without proposing choices. It must not repeat A1's four schemes. A second question about collision prevention stays in A2 and also needs no option list; numbered procedural steps are allowed as explanation. If A2 later proposes three issuance methods, subsequent clarifications there repeat those three methods only. A return to A1 restores its four schemes with their original numbers, current statuses, and node references.

### Developing and Revising a Comparison

Apply [Build the Comparison Before Recommending](../SKILL.md#build-the-comparison-before-recommending) when forming the initial comparison or materially revising it. Use Context Consistency And Impact for comparative conclusions: Applicable Baseline identifies the criteria that make alternatives consequential; Consistency assesses candidate compliance under stated conditions; Dependencies And Impact identifies affected recommendations; Evidence For Consequences assesses support for comparative claims and material gaps in the examined alternatives. Reuse applicable findings. This uses the existing checks without adding a mandatory `Phase Agent Check` or asking the user to approve the candidate search.

For example, assume the node owning an initial naming comparison is current and covers reserved sequential numbers, assigned namespaces with local counters, and UUIDv7. Locally generated identifiers are within scope, and date plus a random suffix is then identified as a missing family. A suitable correction is:

> The comparison omitted date plus a random suffix. This adds a candidate; it does not record a scheme choice. The visible date and the identifier-generation mechanism are separate properties. Its generation and duplicate-handling procedure need assessment against the same uniqueness criterion used for the other candidates.
>
> **1. Reserved sequential numbers — under consideration**
>
> ---
>
> **2. Assigned local namespaces — under consideration**
>
> ---
>
> **3. UUIDv7 identifier scheme — under consideration**
>
> ---
>
> **4. Date and random suffix — under consideration**
>
> My earlier preference for UUIDv7 for local creation needs reassessment alongside this family. I recommend comparing the two local-generation approaches next because the omitted family could change that recommendation; neither brevity nor a visible date is a mandatory requirement unless the input establishes it.

This is an abbreviated illustrative response body, not a required candidate set or authorization to resume an unselected request. The numbered blocks abbreviate the candidate explanations; apply the [content preservation rules](#preserve-node-content-on-return) to show the complete revised body and retain unaffected explanations in the actual response. The quotation marks this documentation example only; do not quote the option blocks in the ordinary response. Prepend the actual discussion path and use the actual stable option titles, local numbers, and node references under the navigation rules. Use actual evidence and candidate statuses; the shared rules govern exclusions, focus, and limited results.

### Focused Analysis Within a Comparison

Apply the shared [return-to-comparison guidance](../SKILL.md#return-to-the-overall-comparison) during candidate analysis in this phase. Use Request Clarity's Subject and Scope findings to distinguish a local configuration choice from scheme selection or exclusion. Use Context Consistency And Impact's Applicable Baseline, Revision Boundaries, Dependencies And Impact, and Evidence For Consequences findings to assess its effect on the overall comparison. Reuse findings that remain valid; this adds no mandatory `Phase Agent Check` or confirmation step.

For example, assume the presented proposal has been accepted under the existing confirmation rules: use four random characters without coordination for `YYYYMMDD-rrrr-topic`, with a previously explained residual collision risk. Sequential numbering, ULID, and UUIDv7 remain open. While discussing suffix length in a node without its own options, a suitable decision note alongside its complete updated body is:

> For `YYYYMMDD-rrrr-topic`, four random characters without coordination are accepted, with the stated residual risk. This configures one candidate; the overall scheme has not been selected.

Retain the other candidates in context without appending their parent list. If the user subsequently returns to the node owning the scheme comparison, show its complete list. A suitable response body at that node is:

> **1. Date and random suffix — under consideration**
>
> **Accepted configuration.** Four random characters without coordination, with the stated residual risk. This is not overall scheme selection.
>
> ---
>
> **2. Sequential numbering scheme — under consideration**
>
> **Comparison gap.** Its mechanism and costs have been examined in less depth.
>
> ---
>
> **3. ULID identifier scheme — under consideration**
>
> **Comparison gap.** Its mechanism and costs have been examined in less depth.
>
> ---
>
> **4. UUIDv7 identifier scheme — under consideration**
>
> **Comparison gap.** Its mechanism and costs have been examined in less depth.
>
> The required ordering within a day is still unresolved.
>
> I recommend examining sequential-number reservation next, to compare its coordination cost with independent random generation.

These illustrate a decision note and an abbreviated comparison after return, not replacements for an existing complete node presentation, a required template, or automatic authorization to navigate or investigate numbering. Apply the [content preservation rules](#preserve-node-content-on-return) to retain the full revised body and unaffected explanations in actual responses. The quotation marks documentation examples only; render actual option blocks without blockquote prefixes. Prepend the actual discussion path for each response and use the actual stable option titles, local numbers, and node references. The recommendation assumes numbering investigation is within the current comparison's scope and is not an unselected request. If it was an unselected request, do not re-offer it merely because numbering remains open; follow the existing [selection and order rules](#selection-and-order). An exclusion or deferral of any listed candidate changes the overview accordingly; do not reuse an illustrative open status against the actual decisions.

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
- A topic reference within one question or result request identifies its Subject; it is not automatically an additional Direct The Interaction intention. For example, "Explain issuance through Git" is one explanation request targeting the previously listed Git option. An explicit return such as "Return to A2" is Direct The Interaction. Independent substantive and control intentions still follow the category-combination rules; navigation does not bypass them.
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

A suitable response body, preceded by the current discussion path, is:

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

Use the feedback attributes and check findings to distinguish an error correction from a proposed change to the user's decisions. Apply [discussion navigation](#discussion-path-and-navigation) to the response path and any list owned by the current node; pending exclusion does not collapse the path or change an option's status.

1. **Correct established errors.** Verify disputed facts and assess consequences under the existing goal and criteria. Correct an established agent error immediately without asking the user to approve the correction. If an option violates a goal or criterion, state the finding and stop recommending it as satisfying that goal or criterion. If the alleged defect is unverified or disproved, report that accurately. None of these findings is itself the user's decision to exclude the option or relax a criterion.
2. **Ask about exclusion for goal or criterion criticism.** When the user criticizes an option's compliance with the investigation's goal or a criterion and inclusion or exclusion is not unambiguous, you must ask one concrete question: exclude the identified option from further consideration, or retain it for comparison with the identified deficiency recorded? Name the exact option or standalone scheme and the boundaries of exclusion; do not extend rejection of one format to its entire family. Where relevant, state which combinations or other options are outside that boundary. If the alleged deficiency is not established, describe it as an allegation or open issue rather than a confirmed defect. Correcting the factual assessment does not fulfill this clarification requirement. An already explicit exclusion request or confirmation needs no repeated question about intent; an explicit request to retain the option also resolves that intention. Apply the existing admission and confirmation rules to any requested change.
3. **Handle other evaluations proportionately.** Outside goal or criterion criticism, ask a focused clarification question only if plausible interpretations would materially change the next step. Otherwise, reflect the user's opinion in the explanation without additional confirmation. Do not create a mandatory exclusion question for every negative assessment.
4. **Make the question concrete.** Formulate the clarification as a `Phase Agent Action Proposal` identifying the exact subject and scope. For the mandatory disposition question, present exclusion and retention for comparison as alternatives rather than presuming rejection. For other consequential feedback, propose the specific plausible change and ask the user to confirm or correct it. Do not first ask a generic question and then request confirmation of the same unchanged interpretation.
5. **Preserve the current decision until the answer.** Keep exclusion separate from accepted decisions until the user answers unambiguously and applicable admission and confirmation requirements are satisfied. Retain the option's current inclusion or exclusion status in the meantime. This does not suppress a verified defect, justify recommending the option as compliant, or prevent correction of its factual assessment. Do not record exclusion as a user decision merely because the user identified a defect.
6. **Apply the answer precisely.** Update only the confirmed subject and scope. Keeping the option for comparison does not withdraw the criterion or establish compliance. An unqualified answer to the concrete proposal satisfies confirmation for that unchanged content; a correction, qualification, or other independent intention requires reassessment under the existing rules. Do not add an intent-clarification round when exclusion has already been explicitly requested or confirmed.

For example, assume the investigation requires unique identifiers and `YYYYMMDD-topic` uses only the date as its identifier. The user says:

> `20261113-topic` assumes the identifier `20261113`, which is not unique at all.

The following illustrates feedback wording and the disposition question. When correcting an existing node presentation, include its complete corrected body between the feedback note and the question under the [content preservation rules](#preserve-node-content-on-return); the excerpt does not replace that body:

> Correct: a date alone does not ensure uniqueness. The following choice concerns only `YYYYMMDD-topic` as a standalone scheme; it does not affect combinations of a date with another identifier.
>
> ❓ **Q1 — Standalone scheme:** Exclude `YYYYMMDD-topic` from further consideration or keep it for comparison with this deficiency noted?
>
> - **A.** Exclude only the standalone scheme `YYYYMMDD-topic`.
> - **B.** Keep it for comparison with the uniqueness deficiency recorded.
> - **C. Custom answer** — Specify another action, correct the scope, or ask a question.
>
> Reply, for example: `Q1: A` or `Q1: C — <your answer>`.

Prepend the actual discussion path. If the current node owns a comparison list, include that complete list with current statuses and own-node references; the criticized scheme retains its existing status while disposition is pending. If discussing the scheme in a child node without its own list, do not append the ancestor's comparison. The factual correction is immediate. Excluding the standalone scheme remains undecided until the answer. Do not broaden this question to all date-based identifiers. If the user instead says "Exclude `YYYYMMDD-topic` as a standalone scheme," apply the existing change-admission and confirmation rules without asking again whether exclusion is intended.

Answer independent questions from the same message in the same response when the category-combination exception applies, alongside the focused disposition question. For example, an independent explanation of UTC need not wait for the exclusion decision. Do not let that answer imply acceptance, rejection, or withdrawal of the criterion. A question whose answer depends on retaining or excluding the option must wait for the relevant clarification; preserve the user's explicit ordering and stopping instructions.

## Explicit Confirmation

For research context within the fixed input boundaries, before adopting newly established or revised context under **Provide Or Revise Context**, present the proposed wording and request explicit confirmation. Until confirmation, distinguish the proposed context from the agreed context.

When this revises an existing node presentation, apply the [full-body revision rule](#preserve-node-content-on-return) both when presenting the proposal and after its valid acceptance. This changes presentation, not the conditions for admission or confirmation below.

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
