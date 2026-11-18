# FocusMatrix Research and Analysis

This plugin provides workflows for preparing research input and briefs. Version `0.1.0` contains three skills:

- [exploration-input-clarification](skills/exploration-input-clarification/SKILL.md) clarifies a request, confirms intent, and saves input for brief creation.
- [exploration-input-validation](skills/exploration-input-validation/SKILL.md) checks supplied exploration Markdown for readiness and reports needed corrections.
- [exploration-brief-creation](skills/exploration-brief-creation/SKILL.md) uses that input to clarify scope and save a confirmed brief with a complete research plan.

These skills do not execute the research or implements a solution.

## Local Authoring and Use

The canonical skills live inside this package. The repository includes these relative development symlinks:

```text
.agents/skills/exploration-input-clarification
  -> ../../plugins/fm-research-and-analysis/skills/exploration-input-clarification
.agents/skills/exploration-input-validation
  -> ../../plugins/fm-research-and-analysis/skills/exploration-input-validation
.agents/skills/exploration-brief-creation
  -> ../../plugins/fm-research-and-analysis/skills/exploration-brief-creation
```

Edits to the canonical files are reflected through the links. The [official skill guide](https://learn.chatgpt.com/docs/build-skills) documents repository-local discovery through `.agents/skills`, symlink support, and explicit invocation. Input clarification's [Codex policy](skills/exploration-input-clarification/agents/openai.yaml) disables implicit invocation. Invoke it explicitly from this repository:

```text
$exploration-input-clarification Help me clarify the exploration request in <input-path>.
```

Input may also be supplied in chat. After each clarification round, the workflow summarizes its understanding and offers relevant categories for further clarification, a custom direction, or finishing. Categories are derived from the current request; optional deepening does not block readiness. Choosing to finish is followed by a separate restatement confirmation. If blocking ambiguities remain, the user may continue clarification, choose to save explicitly incomplete input, or stop without saving. Incomplete saving requires separate confirmation of the partial understanding and gaps and does not complete clarification or establish readiness for brief creation.

The skill's [main workflow](skills/exploration-input-clarification/SKILL.md) owns dialogue stage transitions and applies the [shared readiness criteria](references/exploration/input-readiness-criterias.md) throughout clarification. Its [dialogue protocol](skills/exploration-input-clarification/references/clarification-dialogue.md) defines Markdown questions, custom answers, answer validation, retries, and intentional deferrals; it is read before the first question of any kind. The [output template](references/exploration/input-template.md) is used before the full preview. The draft is checked against the dialogue. Completed input then requires [validation without the clarification history](references/exploration/isolated-validation.md) before confirmation. If a separate agent cannot start, the workflow tells the user and waits for a check in a new chat.

Saving uses a user-specified destination or the host's configured saving convention; otherwise the workflow asks for a destination when needed.

## Input Validation

Invoke `$exploration-input-validation Check <input-path>.` or supply the Markdown text. The skill evaluates the current document without the original conversation. It returns `PASS` or `FAIL` using the [result template](references/exploration/validation-result-template.md). A consuming workflow checks the current Markdown in a clean session or with a separate agent and reports the problems and needed corrections to the user on failure and waits for revised input. All shared files are part of the installed plugin.

## Brief Creation

Invoke `$exploration-brief-creation Prepare a research brief from <clarified-input-path>.` or supply the saved Markdown content. Brief creation uses default automatic discovery; the existing input-clarification skill retains its explicit-only policy. The [brief workflow](skills/exploration-brief-creation/SKILL.md), [dialogue protocol](skills/exploration-brief-creation/references/brief-dialogue.md), and [template](skills/exploration-brief-creation/references/brief-template.md) are bundled resources.

The shared [communication and writing style](skills/exploration-brief-creation/SKILL.md#communication-and-writing-style) applies to every user-facing message and question, including answer options, checkpoints, progress updates, limitations, and saving reports, as well as the entire brief. It calls for ordinary working language while preserving technical precision and the status of requirements, preferences, and hypotheses. Question layout remains defined by the dialogue protocol.

After input validation passes, the workflow asks whether to inspect existing project documents and code or use **Greenfield Zone**. It waits for an explicit choice before project discovery. Authorized inspection is targeted and read-only, stopping when context suffices to frame research. Greenfield Zone uses the supplied input and dialogue without inspecting existing project materials; both modes operate within the repository. The mode describes brief preparation and does not grant permission for later research access.

The skill proposes decomposition, questions, scope, methods, and completion criteria, then clarifies material gaps with the user. It preserves distinctions between the primary problem, its occurrence conditions, and consequences, and checks how agent-added directions could change the user's conclusions or decisions. Unknown research directions may be handled by a bounded initial mapping stage.

Before showing directions, the skill checks for duplicated work and conflicting assumptions, scope, or outputs, then orders review by dependencies. It presents one direction at a time, with one or two explanatory paragraphs, research steps, a separate expected-output section, and a short example. Research steps have no fixed count: related checks are grouped by question or intermediate result, then reviewed for unnecessary splitting without hiding material methods, dependencies, or outputs. The user can shorten the list, combine items, or remove specific steps. The agreed list is retained as `Research steps` in the saved brief. The overall plan connects directions without repeating their local lists. The expected output may use one or two paragraphs or a bullet list where helpful. Research labels appear only beside direction titles on their first line; references elsewhere use titles.

The user confirms the current description or requests changes before the skill advances. The user can add, remove, merge, split, narrow, or clarify directions and revise their research steps. Changes trigger renewed review of affected directions and a check of remaining dependencies and expected outputs; unaffected confirmations are retained. After edits, the same response shows the complete updated direction under its existing label and title, including all current steps. A shorter list is not refilled to meet a quota; substantive gaps caused by removals are clarified with the user. A change summary does not replace the full display. Ambiguous or conflicting passages have inline notes in an explicitly marked working version; only necessary clarification questions follow, with confirmation withheld until material blockers are resolved. A request solely for explanation does not require redisplay if content is unchanged, and explicit removal retains its existing handling.

When a change conflicts with earlier answers, the workflow explains which answers are affected and reopens only those questions in dependency order. Unrelated answers remain accepted. After new answers, the complete current direction is shown again for clarification or explicit confirmation as appropriate. The saved source input is not rewritten automatically. The agreed descriptions, research steps, expected outputs, and examples remain in the saved brief. After individual review, finishing clarification and confirming the full brief remain separate; there is no collective list-confirmation checkpoint. Successful saving is still required. Incomplete input and unresolved user decisions cannot be silently treated as ready. Saving failures leave the workflow incomplete. Research does not start automatically after saving.

Feedback on a complete brief uses the [post-brief revision cycle](skills/exploration-brief-creation/SKILL.md#revisit-directions-after-full-brief-feedback). Each affected direction gets a specific explanation of the correction and its impact, followed by the complete direction with [inline editorial markup](skills/exploration-brief-creation/references/brief-dialogue.md#show-post-brief-revisions) for additions, changes, and removals. Comparison uses the direction text from the latest full-brief confirmation presentation, held fixed across clarification rounds and individual confirmations. Each subsequent full-brief confirmation presentation establishes new baselines. Initial direction review before the first complete brief does not use these additions. Further corrections repeat dependency, consistency, and readiness checks. Reason blocks and revision markup are dialogue-only: the full brief for confirmation and saved documents contain clean current content, with required status and blockers retained for unfinished drafts.

## Clarified Input Output

Completed input is a self-contained Markdown document for the next agent preparing a brief. Its [template and filling rules](references/exploration/input-template.md) define a descriptive title, a required confirmed request, and conditional sections for context, conditions, unconfirmed proposals, and future research questions. Section names are fixed in English. Material clarifications and explicit deferral decisions are incorporated directly into the current understanding, without a dialogue history or a separate list of brief-preparation questions. The incomplete variant uses the same headings with a required status notice, only the confirmed partial understanding, and visible unresolved blockers; consumers stop on its failed readiness check.

## Package and Verification Status

The canonical [plugin.json](plugin.json) follows the portable format in the [official packaging guide](https://developers.openai.com/plugins/build/plugins). Skills are packaged under `skills/`; the package has no scripts, bundled tools, or external service prerequisites. Reading supplied input and saving the result require capabilities provided by the host.

The development link supports local authoring; it does not install the distributable plugin. The installed package uses its own files and does not depend on the link or repository governance. No marketplace catalog or installation settings are included in this change.

Prior verification of input clarification includes static instruction comparison, a passage-by-passage requirement map, and 13 manual scenario walkthroughs covering readiness, clarification, answer handling, confirmation, and saving. The brief skill has static instruction and resource checks and manual scenario review covering mode selection, discovery boundaries, research framing, confirmation, and persistence. All three skills pass the standard skill validator. Codex CLI 0.170.0 installed the package from a temporary marketplace into an isolated configuration. The runtime discovered all three installed skills, and their shared references resolved inside the installed copy. Read-only Codex sessions exercised the installed instructions on complete, incomplete, and missing input. The validator returned the expected report for each case. The consuming workflow reported the incomplete input blocker and stopped before project discovery when instructed to apply the shared checks directly. A subsequent Codex run stopped when the current Markdown omitted a source boundary discussed in the parent session. In a simulated disabled-agent run, the consuming workflow displayed the draft and requested a new-chat report. A fresh validator session passed the corrected input and rejected incomplete input.

The existing development evaluator does not cover round menus, answer-validation retries, or incomplete saving. Its pre-confirmation command check recognizes only direct `cat …/SKILL.md` reads, so reading the dialogue reference also requires adaptation before its results can validate this contract. The evaluator is unchanged.

Codex is the initial packaging target; portability of the instructions does not establish support for other hosts. See the [changelog](CHANGELOG.md) for changes.
