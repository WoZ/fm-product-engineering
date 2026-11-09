---
name: exploration-brief-creation
description: Turn saved clarified exploration input into a confirmed research brief with a complete research plan. Ask whether to inspect existing project documents and code or use Greenfield Zone, then clarify scope, questions, methods, and completion criteria. Excludes initial intent clarification, research execution, and implementation.
---

# Exploration Brief Creation

Prepare a self-contained brief that another researcher can execute without reconstructing chat history. Exploration may seek understanding, explanation, a map of options, comparison, or a recommendation; do not require comparison or solution selection for every task.

Read [the brief dialogue protocol](references/brief-dialogue.md) before asking any question. Use it for missing input, mode selection, clarification, checkpoints, confirmation, and saving. Read [the brief template](references/brief-template.md) when assessing completeness and preparing the document.

Preserve the input's intent, decisions, exclusions, qualifications, and explicit deferrals. Preferences remain optional, user assertions remain attributed where needed, and hypotheses remain unverified. Proposals become agreed conditions only through user acceptance. Do not silently resolve conflicts or replace the user's problem.

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

Ask related groups of precise questions whose answers materially change the framing or plan. Prioritize intended use, applicable scenarios, boundaries, constraints, priorities, depth, available resources, and sufficiency. Do not re-ask answered questions, populate irrelevant template sections, or require the user to supply findings that research is meant to establish.

Distinguish:

- **User decisions:** Intent, permission, priorities, and acceptable tradeoffs that evidence alone cannot establish. Ask when an unresolved choice materially changes the task.
- **Discoverable context:** Facts available through authorized inspection; read them instead of asking the user to repeat them. Preserve uncertainty if they cannot be verified.
- **Research unknowns:** Facts, explanations, candidate approaches, and feasibility questions the research must resolve. Place them in the plan with a way to investigate them.

For each significant subquestion, connect its purpose to a method, required data or sources, expected output, and a sufficiency criterion. Establish priorities and dependencies. Choose methods appropriate to the subject; interviews, experiments, and code analysis are not universal requirements. Distinguish solution costs and constraints from research resources and limits.

If relevant directions cannot be identified without substantive research, plan an initial mapping stage. Define its question, limits, inclusion and exclusion criteria, expected output, and conditions for selecting directions for deeper investigation. Do not invent a final candidate list or demand that the user choose unknown alternatives. A complete plan can contain explicit evidence-dependent branches and an initial access or feasibility check.

Define evidence expectations proportional to the task, including how findings will distinguish evidence from interpretation, handle contradictions, and report remaining uncertainty. Do not impose arbitrary source counts, candidate counts, stage counts, or numeric confidence scores.

After each group is answered or explicitly deferred, summarize material changes and remaining blockers. Offer relevant further clarification, a user-supplied direction, or finishing when ready. Wait for the user's choice before optional deepening or final confirmation. Do not manufacture questions to prolong the dialogue.

## 4. Check Readiness and Confirm the Brief

A brief is ready for confirmation only when:

- Purpose, intended consumer, expected use, and required outcome are clear.
- Scope, exclusions, mandatory conditions, and material preferences are preserved and sufficiently defined to bound the work.
- Significant questions connect to the goal and have a workable investigation path, including explicit checks or branches where necessary.
- Sources, data needs, dependencies, research limits, expected outputs, and completion criteria are sufficiently specified to start.
- No hidden decision about user intent or permission remains. Material assumptions and unresolved research questions have visible status and handling.

Unanswered research questions are expected. An unknown blocks readiness only when no bounded plan can handle it without an unsupported user decision or essential unavailable prerequisite. Clarify such blockers; optional depth and template completeness alone do not create blockers. Explicit deferral does not resolve a blocker or authorize research into it.

The researcher may refine methods and add subquestions within the agreed goal, scope, constraints, and resources, recording consequential adjustments in the research output. Changes outside those boundaries require user agreement. Include this rule in the brief.

When the user chooses to finish and the brief is ready, prepare it using the template and present the full document for explicit confirmation. A finish choice, approval of an earlier outline, or inspection permission does not confirm the final brief. After substantive corrections, reassess readiness and obtain confirmation of the revised document. If the user stops earlier, leave the workflow incomplete; an explicitly requested draft must be labeled as not ready, with visible blockers.

## 5. Save and Hand Off

After confirmation, save the current brief to the user's destination or the host's configured saving convention. Ask for a destination if neither exists. Do not overwrite an existing artifact without authorization. A narrow existence check at the selected destination is allowed in both modes; it does not permit reading other project content. Do not alter the source input.

If persistence fails or is unavailable, provide the prepared content in chat and state that saving remains incomplete. Do not claim persistence or workflow completion.

Complete only when the current brief is ready, explicitly confirmed, and successfully saved. Report its location and material unverified prerequisites. Stop without starting research, implementation, or another workflow.
