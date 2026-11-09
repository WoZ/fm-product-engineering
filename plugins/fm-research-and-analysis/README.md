# FocusMatrix Research and Analysis

This plugin provides workflows for preparing research input. Version `0.1.0` contains one skill: [exploration-input-clarification](skills/exploration-input-clarification/SKILL.md), which clarifies a request, obtains confirmation of the user's intent, and saves the input for brief creation. It does not create a brief or conduct research.

## Local Authoring and Use

The canonical skill lives inside this package. The repository includes this relative development symlink:

```text
.agents/skills/exploration-input-clarification
  -> ../../plugins/fm-research-and-analysis/skills/exploration-input-clarification
```

Edits to the canonical files are reflected through the link. The [official skill guide](https://learn.chatgpt.com/docs/build-skills) documents repository-local discovery through `.agents/skills`, symlink support, and explicit invocation. The skill's [Codex policy](skills/exploration-input-clarification/agents/openai.yaml) disables implicit invocation. Invoke it explicitly from this repository:

```text
$exploration-input-clarification Help me clarify the exploration request in <input-path>.
```

Input may also be supplied in chat. After each clarification round, the workflow summarizes its understanding and offers relevant categories for further clarification, a custom direction, or finishing. Categories are derived from the current request; optional deepening does not block readiness. Choosing to finish is followed by a separate restatement confirmation. If blocking ambiguities remain, the user may continue clarification, choose to save explicitly incomplete input, or stop without saving. Incomplete saving requires separate confirmation of the partial understanding and gaps and does not complete clarification or establish readiness for brief creation.

The skill's [main workflow](skills/exploration-input-clarification/SKILL.md) owns readiness and stage transitions. Its [dialogue protocol](skills/exploration-input-clarification/references/clarification-dialogue.md) defines Markdown questions, custom answers, answer validation, retries, and intentional deferrals; it is read before the first question of any kind. The [output template](skills/exploration-input-clarification/references/clarified-input-template.md) is read after restatement confirmation. All three resources are bundled in the package.

Saving uses a user-specified destination or the host's configured saving convention; otherwise the workflow asks for a destination when needed.

## Clarified Input Output

Completed input is a self-contained Markdown document for the next agent preparing a brief. Its [template and filling rules](skills/exploration-input-clarification/references/clarified-input-template.md) define a descriptive title, a required confirmed request, and conditional sections for context, conditions, unconfirmed proposals, and future research questions. Section names are fixed in English. Material clarifications and explicit deferral decisions are incorporated directly into the current understanding, without a dialogue history or a separate list of brief-preparation questions. The incomplete variant uses the same headings with a required status notice, only the confirmed partial understanding, and visible unresolved blockers; consumers must not treat it as completed input for brief creation.

## Package and Verification Status

The canonical [plugin.json](plugin.json) follows the portable format in the [official packaging guide](https://developers.openai.com/plugins/build/plugins). Skills are packaged under `skills/`; the package has no scripts, bundled tools, or external service prerequisites. Reading supplied input and saving the result require capabilities provided by the host.

The development link supports local authoring; it does not install the distributable plugin. The installed package uses its own files and does not depend on the link or repository governance. No marketplace catalog or installation settings are included in this change.

Verification includes static instruction comparison, a passage-by-passage requirement map, and 13 manual scenario walkthroughs covering readiness, clarification, answer handling, confirmation, and saving. Local package links and anchors were checked. The standard skill validator could not run because the available Python environment lacks `PyYAML`. Runtime discovery, plugin installation, and live behavioral execution have not been verified.

The existing development evaluator does not cover round menus, answer-validation retries, or incomplete saving. Its pre-confirmation command check recognizes only direct `cat …/SKILL.md` reads, so reading the dialogue reference also requires adaptation before its results can validate this contract. The evaluator is unchanged.

Codex is the initial packaging target; portability of the instructions does not establish support for other hosts. See the [changelog](CHANGELOG.md) for changes.
