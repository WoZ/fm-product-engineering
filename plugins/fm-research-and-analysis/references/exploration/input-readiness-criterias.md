# Exploration Input Readiness Criteria

Assess the current understanding during clarification or the supplied Markdown during document validation. Use only the information available to the current check. A request is ready when it has an investigative or learning component, the primary intent, subject, and expected outcome are understood, applicable research modes and required project-source boundaries are determined, and no blocker remains. A fixed solution alone does not make a request unsuitable for exploration.

## Diagnostic Criteria

Evaluate all ten criteria. These are diagnostic checks, not required artifact fields, fixed clarification categories, or a user questionnaire:

1. **Intent:** Desired achievement and stated motivation.
2. **Problem or need:** Underlying problem, need, or curiosity, where relevant.
3. **Expected understanding or decision:** What the user wants to learn, explain, describe, or decide.
4. **Context:** Whether supplied context suffices to interpret the request.
5. **Scope:** Intended subject, boundaries, and exclusions.
6. **Constraints:** Explicit mandatory requirements, constraints, and preferences.
7. **Ambiguity:** Key terms with materially different interpretations.
8. **Consistency:** Contradictions preventing an accurate document preview.
9. **Assumptions:** Unconfirmed assumptions about intent.
10. **Research suitability:** Investigation or learning versus solely executing an already defined task.

Missing detail is not automatically blocking. Distinguish understanding the request from designing or conducting research.

## Determine Research Mode for the Subject

Once the research goal and subject are clear, determine the mode before assigning `READY` whenever it changes what the user wants investigated. Apply this check to each part of the project for which the user expects a distinct conclusion or decision. A component mentioned only as a compatibility constraint does not need its own mode. Skip the check when the choice does not change the task, such as explaining how an existing system behaves.

- **Greenfield** explores a solution designed from scratch within any stated boundaries.
- **Brownfield** explores changes that take the existing solution as their starting point.
- **Comparison of Greenfield and Brownfield** explores both paths when the research should inform the choice between them.

Use a mode the user states or that follows unambiguously from the request. Establish the goal and subject first. An unresolved applicable mode blocks handoff, including after an explicit deferral. An explicit request to compare both paths determines the mode and leaves the choice of approach to research. In completed Markdown, each applicable mode must be explicit and tied to its subject.

## Clarify Permitted Research Sources

Once the research goal and subject are clear, check whether there are material conditions on the sources the researcher may use. Treat this as a separate decision from the research mode. By default, assess source boundaries for research execution. Preserve any scope the user explicitly sets for research execution or preparation.

When the request concerns a specific existing project and its materials could materially affect the research, require a decision on whether and within what scope the researcher may independently inspect those materials before assigning `READY`. This applies even when the goal and expected outcome are already clear. For example, existing directory names or allocated identifiers can inform the design of a new naming scheme for the current repository. A generic request about naming in Git repositories needs no project-source decision.

An unresolved required project-source boundary blocks handoff, including if the user defers the decision to a later stage. Completed Markdown must state the boundary explicitly. Research mode, silence, and delegation do not grant permission to inspect sources.

Apply the Blocker Test to other source uncertainties. Assess external sources separately when material. A limit on repository inspection leaves the use of external sources undecided unless the user specifies it. If the other source choices can wait until a later stage without changing the task, allow `READY` when the other criteria are met and preserve any explicit delegation.

When describing a source limit, distinguish gathering project evidence from reading applicable workspace instructions and any conventions they require. The limit on gathering evidence does not prevent the researcher from consulting those instructions as needed to follow them. Preserve applicable mandatory rules that constrain the outcome. Using examples, descriptions of current project behavior, or linked materials as research evidence remains subject to the agreed source limits.

## Blocker Test

After checking the required research mode and project-source boundary, apply all three checks internally to each remaining material uncertainty before assigning `READY` or classifying a question as blocking:

1. **Unresolved meaning:** Identify two plausible interpretations grounded in the input and how they change subject, scope, or outcome. For missing primary intent or conflicting requirements, identify what cannot be understood or reconciled instead of inventing alternatives.
2. **Unavoidable choice:** Identify the unsupported assumption or user decision needed for handoff. Explain why its absence would convey materially different tasks; an effect on research framing, findings, or implementation alone is insufficient.
3. **Faithful handoff:** Can the uncertainty remain open while conveying the same understood task and preserving stated conditions? Available funds are not automatically a spending cap; a desired date is not automatically a deadline. Neither a broad umbrella paraphrase nor silently delegating unknown intent to research resolves ambiguity.

Only a failure to hand off accurately makes the question blocking. Otherwise retain the gap without inventing an answer.

## Nonblocking Gaps

- **Research framing:** Leave research framing and planning to a later stage. Preserve stated decisions that affect that work. Optional framing details do not block the handoff.
- **Exploration:** Leave facts, explanations, comparisons, and findings to research. Preserve already identified questions that add material meaning beyond the confirmed request.

For each material gap left open in completed input, identify why it does not obscure intent. An unanswered question or a research-question label does not establish delegation to research; resolve unclear delegation when it changes the task. Conversely, do not require the user to choose what research is intended to compare or inform.

Optional gaps and unselected categories do not block readiness merely because they affect eventual research.
