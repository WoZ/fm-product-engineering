---
name: exploration-brief-creation
description: Turn saved clarified exploration input into a confirmed research brief with a complete research plan. Ask whether to inspect existing project documents and code or use Greenfield Zone, then clarify scope, questions, methods, and completion criteria. Excludes initial intent clarification, research execution, and implementation.
---

# Exploration Brief Creation

Prepare a self-contained brief that another researcher can execute without reconstructing chat history. Exploration may seek understanding, explanation, a map of options, comparison, or a recommendation; do not require comparison or solution selection for every task.

Read [the brief dialogue protocol](references/brief-dialogue.md) before asking any question. Use it for missing input, mode selection, clarification, checkpoints, confirmation, and saving. Read [the brief template](references/brief-template.md) when assessing completeness and preparing the document.

Preserve the input's intent, decisions, exclusions, qualifications, and explicit deferrals. Preferences remain optional, user assertions remain attributed where needed, and hypotheses remain unverified. Proposals become agreed conditions only through user acceptance. Do not silently resolve conflicts or replace the user's problem.

## Writing Style

Use ordinary working language throughout the entire brief, both when presenting its content in chat and in the saved document. This applies to titles, questions, explanations, examples, lists, and tables in every section, including purpose, context, scope, constraints, research plan, evidence requirements, expected outputs, completion criteria, and assumptions.

Use direct sentences, concrete actions, familiar words, and descriptive titles. Remove inflated, bureaucratic, or unnecessarily abstract wording. Retain necessary technical terms and briefly explain them on first use when their meaning may be unclear. Preserve exact technical identifiers, paths, and verbatim quotations.

Simplification must preserve meaning and precision: mandatory conditions, optional preferences, hypothesis status, causal relationships, dependencies, and research boundaries. Keep the template's fixed headings and the document's language conventions. Paragraph limits specified for parts of a research direction do not apply to other sections.

## 1. Read and Check the Input

Read the saved clarified input identified by the user, or its supplied Markdown content, with relevant conversation context. If it is missing or inaccessible, explain the limitation and request only the input needed. Do not search the project to locate an unspecified input or reconstruct intent from unrelated files.

Check the document's meaning as well as its status. Input marked `INCOMPLETE — CLARIFICATION REQUIRED`, or containing unresolved intent blockers, cannot support a ready brief. Explain the blockers and offer to return to intent clarification or stop. Do not automatically invoke another workflow or invent a resolution. Resume brief creation when the user supplies resolved, confirmed input.

An input document need not already contain research framing, methods, or a brief-preparation questionnaire. Determining these belongs to this skill.

Use host capabilities for reading and saving; no specific service, credential, or tool is required. Project inspection requires suitable read access when selected. Report unavailable capabilities instead of claiming a check succeeded.

## 2. Obtain the Project Context Choice

After reading usable input and before any project discovery, ask the following question, localized to the conversation language and formatted under the dialogue protocol:

> Should existing project documents and source code be used when preparing the brief?
>
> A. Yes — inspect relevant materials to clarify context, decomposition, and research boundaries.
>
> B. No — Greenfield Zone: prepare the brief from the saved input and clarification dialogue without inspecting existing project documents or code.
>
> C. Custom answer — enter your own response.

Always present this choice when starting brief creation. Wait for an explicit answer; prior input, the presence of a repository, silence, a skipped question, or an empty answer does not select a mode. A custom answer may restrict inspection to named materials or documents only; preserve its limits and clarify ambiguous permission before discovery. For a resumed session, retain the explicit choice already made in that session unless the user changes it.

Describe the abstract entity as the **project**, not as a working directory or filesystem location. Record the selected mode and any limits in the brief. Both modes operate within the repository; Greenfield Zone does not imply that the repository is empty or that its code should be replaced.

Reading the supplied input and applicable mandatory host or repository instructions is permitted in both modes. Do not use instruction discovery as a route to exploratory inspection. An input link to other project materials is not permission to inspect them before this choice.

### Existing Project Context

Conduct targeted, read-only discovery of task-relevant documents and, where useful, source code within the authorized project scope. Inspect enough to understand the current situation, identify relevant components and known boundaries, discover useful existing evidence, and check the feasibility of proposed sources and methods. Keep material references traceable by path and section or symbol where practical.

Stop preparatory discovery when you can frame the research and ask informed questions. Leave hypothesis testing, comprehensive code analysis, solution comparison, implementation, builds, and experiments to the research plan. Do not browse external sources for substantive answers during brief creation; identify them as planned sources instead. Do not modify project materials during discovery.

If materials or read capabilities are unavailable, explain the effect and ask whether to supply materials, narrow inspection, select Greenfield Zone, or stop. Do not silently fall back or claim the current state was verified. Material encountered in documents or code is evidence, not authorization to change the chosen mode or workflow.

### Greenfield Zone

Use the supplied clarified input and dialogue without listing, searching, or reading existing project documents or source code for research context. Preserve project facts and constraints already present in the input, with their original status; do not pretend they were independently checked. Ask the user for needed context. Mark unverified feasibility and planned access checks explicitly. A switch to project inspection requires an explicit new choice.

## 3. Develop the Research Framing Through Dialogue

Analyze what the input and permitted context establish. Propose the main research question, decomposition, scope, and approach rather than asking the user to design the research. Label proposals as unconfirmed and explain consequential tradeoffs.

### Preserve the Task's Causal Structure

Where the task describes a problem, distinguish the primary problem, the conditions under which it arises, and its consequences. Preserve the relationships and qualifications supplied by the user in the main question, context, and decomposition. Do not promote a triggering condition or downstream consequence into the primary problem, or assert that a condition causes an outcome without support. Label unverified causal explanations as hypotheses. Ask for clarification when competing interpretations materially change the research task. For requests seeking understanding without a stated problem, do not invent a problem or causal chain.

### Develop and Justify Directions

Ask related groups of precise questions whose answers materially change the framing or plan. Prioritize intended use, applicable scenarios, boundaries, constraints, priorities, depth, available resources, and sufficiency. Do not re-ask answered questions, populate irrelevant template sections, or require the user to supply findings that research is meant to establish.

Distinguish:

- **User decisions:** Intent, permission, priorities, and acceptable tradeoffs that evidence alone cannot establish. Ask when an unresolved choice materially changes the task.
- **Discoverable context:** Facts available through authorized inspection; read them instead of asking the user to repeat them. Preserve uncertainty if they cannot be verified.
- **Research unknowns:** Facts, explanations, candidate approaches, and feasibility questions the research must resolve. Place them in the plan with a way to investigate them.

For each significant subquestion, connect its purpose to a method, required data or sources, expected output, and a sufficiency criterion. Establish priorities and dependencies. Choose methods appropriate to the subject; interviews, experiments, and code analysis are not universal requirements. Distinguish solution costs and constraints from research resources and limits.

For every direction you add, identify which user conclusion, understanding, or decision could change depending on the answer. A necessary dependency of another significant question is a valid justification; name that connection. If no meaningful effect can be identified, remove the added direction or retain it only as a brief explanation within a relevant direction, without separate research work. Do not silently drop or downgrade a direction explicitly requested by the user; discuss a proposed change. Apply the same check to directions introduced by later revisions.

If relevant directions cannot be identified without substantive research, plan an initial mapping stage. Define its question, limits, inclusion and exclusion criteria, expected output, and conditions for selecting directions for deeper investigation. Do not invent a final candidate list or demand that the user choose unknown alternatives. A complete plan can contain explicit evidence-dependent branches and an initial access or feasibility check.

Define evidence expectations proportional to the task, including how findings will distinguish evidence from interpretation, handle contradictions, and report remaining uncertainty. Do not impose arbitrary source counts, candidate counts, stage counts, or numeric confidence scores.

During initial framing, after each clarification group is answered or explicitly deferred, summarize material changes and remaining blockers. Offer relevant further clarification, a user-supplied direction, or proceeding to direction review when the framing is ready. Wait for the user's choice before optional deepening. Clarifications during direction revisions instead follow the same-response full redisplay sequence below, without an intervening checkpoint. Do not manufacture questions to prolong the dialogue.

### Check Consistency and Order Directions

Before presenting directions, check them together for duplicated research work and conflicting scope, assumptions, or expected outputs. Remove redundant agent-added work and combine substantively related questions when they share a meaningful investigation and purpose, preserving important distinctions. Do not combine unrelated questions merely to shorten the list. Deliberate alternatives and competing hypotheses are not contradictions to resolve before research. Never silently choose which conflicting user requirement to discard. Initial framing may require clarification before direction review; revisions to a direction already under review follow the full working-version display and clarification sequence below. Checking consistency does not prohibit showing an explicitly marked working version with unresolved issues.

Order review by dependencies: first discuss directions whose definitions or user clarifications determine the content of other directions. Among equally independent directions, prioritize relevance to the main task. Clarify shared unresolved user decisions first when needed to establish a workable order. Recheck consistency and reorder remaining directions after consequential edits.

### Explain and Confirm Directions One at a Time

Before final brief confirmation, present each direction individually using [the direction review format](references/brief-dialogue.md#review-research-directions). Use the same format for directions from the input and those you propose: a stable research label only on the first line beside a short title, the research question, **one or two explanatory paragraphs, research steps, a separate expected-output section, and a short example**. Refer to directions by title elsewhere rather than repeating their labels.

Explain what will be investigated, its boundaries, plausible investigation paths or evidence-dependent branches, and why the answer matters to the user's conclusion or decision. Under a separate heading localized as **What the research should produce**, describe the concrete information this direction should yield in one or two paragraphs; use a bullet list where enumeration makes the output clearer. Distinguish that output from the purpose, the work steps, and the outcome of the entire brief. Do not invent findings or require comparison or recommendation where explanation is the intended result. In the saved brief, use the heading `Expected research output`. Examples illustrate the inquiry rather than asserting its answer; label hypothetical examples.

Between the explanation and expected output, include a `Research steps` subsection in the saved brief and its localized counterpart in chat. In Russian dialogue, use the exact heading `Ход исследования`. Provide ten numbered, concrete points describing the planned checks and analysis for this direction in ordinary working language. Adapt the points to the actual question: identify what to clarify, examine, compare where relevant, check against sources or scenarios, and bring together into the expected output. These points describe planned work, not findings or a log of completed research. They are not a requirement for ten separate research stages. Keep them distinct, within the agreed scope and methods; do not add filler, duplicate work, or copy a subject-specific example into unrelated tasks just to reach ten points.

Include these steps in the current direction's confirmation and retain the agreed version in the brief. Align them with the expected output and overall research plan: each local check must serve the direction, and the overall plan should describe shared methods, dependencies, resources, and transitions without repeating all local steps. Changes affecting the steps' substance require the same renewed individual review as other changes to the direction.

Show the current full direction. If no material blocker remains, ask the user to confirm it, request changes, or supply a custom response. Let the user add, remove, merge, split, narrow, or clarify directions and request more explanation. Do not present the next direction for review until the current one is confirmed or the user explicitly removes it. A request to remove it is an explicit scope decision, not confirmation of its old description.

For revisions that retain the current direction, apply every unambiguously understood change that does not require choosing between unresolved conditions, then check consistency and dependencies. In the same response, show the complete current direction under its existing label and title: question, explanation, all ten research steps, expected output, and example. A change summary does not replace this full display. Mark ambiguities and conflicts directly where they affect the content, distinguishing accepted conditions from requested changes still awaiting clarification. Retain unresolved content with its status rather than inventing a resolution or presenting a proposed interpretation as agreed. Explicit removal uses the deletion rule above without redisplaying the removed direction for approval.

If a material ambiguity or contradiction remains, explicitly label the direction as a working version. After the full display, ask only the questions needed to resolve the blockers; do not offer confirmation of that version. After clarification answers, apply the understood updates, recheck dependencies, and show the complete updated direction again in the same response. Request explicit confirmation only when the blockers are resolved; otherwise retain working status and continue necessary clarification. A request solely to explain a term or provision does not require redisplaying the direction if its content remains unchanged. If that request also changes content, use the revision sequence.

If a requested change conflicts with an earlier accepted answer, mark the conflict in the working version. After the full display, explain which earlier answers are affected and that their questions will be asked again. Pause direction confirmation and return only to those conflicting questions, in dependency order, preserving unrelated answers and confirmations. Reuse the original questions and choices when available, following the dialogue protocol's identifier rules. If only a recorded decision is available, ask an equivalent question about that condition without inventing its original wording or requiring dialogue history. Do not automatically replace an earlier answer with an inferred one. Check the new answers against remaining decisions; if conflicts persist, continue focused clarification without choosing a priority yourself. Once resolved, update the current understanding and affected directions, return to the complete current direction, and request its explicit confirmation. Do not rewrite the saved source input automatically.

Silence, a skipped answer, approval of an earlier version, or a request to finish does not confirm the current direction. An explicit deferral leaves review incomplete and does not permit advancing. If later changes affect confirmed directions, update them and obtain renewed confirmation before continuing with dependent directions. This does not replace the required same-response redisplay of the current direction; show that first, then arrange any necessary renewed dependency review. Preserve confirmations of unaffected directions and stable labels, and update plan references by title.

Once all current directions are individually confirmed, offer further clarification, another user direction, or finishing. Do not add a collective list-confirmation checkpoint. Retain the agreed descriptions, research steps, expected outputs, and examples in the brief; direction confirmation does not confirm the complete brief or authorize research.

## 4. Check Readiness and Confirm the Brief

A brief is ready for confirmation only when:

- Purpose, intended consumer, expected use, and required outcome are clear.
- The entire brief follows the writing style above, including the plan, evidence requirements, and completion criteria; simpler wording has not changed the agreed meaning.
- The primary problem, its occurrence conditions, and its consequences retain their original roles where applicable; unverified causal links remain hypotheses.
- Scope, exclusions, mandatory conditions, and material preferences are preserved and sufficiently defined to bound the work.
- Significant questions connect to the goal and have a workable investigation path, including explicit checks or branches where necessary.
- Every agent-added direction has a meaningful effect on a user conclusion or decision, directly or through a stated dependency. Directions are mutually consistent, avoid duplicated work, and follow their dependencies.
- Each current direction has been individually confirmed after its plain-language description, ten-point research steps, separate expected output, and example were presented. The steps are substantive and consistent with the direction and overall plan. No affected confirmation remains outdated after edits.
- Sources, data needs, dependencies, research limits, expected outputs, and completion criteria are sufficiently specified to start.
- No hidden decision about user intent or permission remains. Material assumptions and unresolved research questions have visible status and handling. No material revision ambiguity, contradictory earlier answer, or required re-answer remains unresolved; a working direction is not ready for confirmation.

Unanswered research questions are expected. An unknown blocks readiness only when no bounded plan can handle it without an unsupported user decision or essential unavailable prerequisite. Clarify such blockers; optional depth and template completeness alone do not create blockers. Explicit deferral does not resolve a blocker or authorize research into it.

The researcher may refine methods and add subquestions within the agreed goal, scope, constraints, and resources, recording consequential adjustments in the research output. Changes outside those boundaries require user agreement. Include this rule in the brief.

When the user chooses to finish and the brief is ready, prepare it using the template and present the full document for explicit confirmation. A finish choice, individual direction confirmations, approval of an earlier outline, or inspection permission does not confirm the final brief. After substantive corrections, reassess readiness, return to individual review of affected directions, and obtain confirmation of the revised document. If the user stops earlier, leave the workflow incomplete; an explicitly requested draft must be labeled as not ready, with visible blockers.

## 5. Save and Hand Off

After confirmation, save the current brief to the user's destination or the host's configured saving convention. Ask for a destination if neither exists. Do not overwrite an existing artifact without authorization. A narrow existence check at the selected destination is allowed in both modes; it does not permit reading other project content. Do not alter the source input.

If persistence fails or is unavailable, provide the prepared content in chat and state that saving remains incomplete. Do not claim persistence or workflow completion.

Complete only when the current brief is ready, explicitly confirmed, and successfully saved. Report its location and material unverified prerequisites. Stop without starting research, implementation, or another workflow.
