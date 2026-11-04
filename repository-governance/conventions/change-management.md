# Change Management

## Purpose and Scope

Make contributions and policy changes concrete and reviewable. Read this convention for the consistency check required with every change, when preparing review, or when changing repository policy.

## Rules

- Agents may author changes; humans review and validate the result. Provide the problem, resulting behavior, verification evidence, and material limitations with the change.
- Read applicable conventions before editing. Keep the change within the authorized task and preserve unrelated work.
- Put requested policy changes in their owning conventions. Check related documents, including root AGENTS.md invariants and routing, and navigation affected by moved documents. Edit related documents only when their update is part of the user's request; otherwise report discrepancies using the procedure below.
- Record significant architectural decisions under `repository-governance/decisions/` using the next available sequence. Include status, context, decision, and consequences. Record supersession when later decisions replace earlier ones.
- Historical decisions and review proposals do not silently amend conventions. Identify policy conflicts explicitly and keep current requirements in conventions. Do not silently choose a new policy to eliminate a conflict.
- Verify affected links, names, package boundaries, and behavioral contracts. Use installation or execution checks when actual packages or executable resources are introduced.
- Do not select a license, publish packages, or configure automated releases as part of initialization.

## Consistency Check for Every Change

1. Identify the requirements and descriptions affected by the requested change, including claims about current repository state.
2. Follow relevant links and search for affected identifiers, paths, and policy terms. Inspect related conventions, AGENTS.md, governance navigation, and README files as applicable; a full reread of unrelated documents is not required.
3. Compare related statements with the intended result and inspect them again against the completed change. Include both existing conflicts discovered during the task and discrepancies introduced by the change.
4. Report each discrepancy with the document and line or section, the conflicting statement, its relationship to the change, and a proposed correction. State any unresolved policy ambiguity rather than silently selecting a rule. Ask for clarification if that ambiguity prevents carrying out the requested task.
5. Report related discrepancies without editing those documents unless their update is part of the user's request. A request explicitly covering synchronization authorizes the corresponding edits. Otherwise, leave them for a separate task and do not claim the affected documentation is fully consistent.

Historical plans, reviews, and decision records describe earlier context. Differences from current policy alone do not require rewriting them. Check that current guidance does not present historical material as governing policy.

In the change report, summarize the documents checked, discrepancies found or none found, and verification limits. This is an agent procedure, not an executable check or a guarantee that every semantic conflict will be found.

## Verification and Review Evidence

For documentation changes, inspect links, naming, language, and rule consistency. A repository status and whitespace review can support that inspection; no persistent validation tooling is required at this milestone.

For future package changes, identify affected plugins and compatibility implications using [Versioning and releases](versioning-and-releases.md). State which checks were actually run; document inspection alone does not establish installation compatibility. Use [Documentation](documentation.md) for document structure.
