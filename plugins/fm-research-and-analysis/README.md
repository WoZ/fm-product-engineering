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

Input may also be supplied in chat. The workflow asks for confirmation of its restatement and uses a user-specified destination or the host's configured saving convention; otherwise it asks for a destination when needed.

## Package and Verification Status

The canonical [plugin.json](plugin.json) follows the portable format in the [official packaging guide](https://developers.openai.com/plugins/build/plugins). Skills are packaged under `skills/`; the package has no scripts, bundled tools, or external service prerequisites. Reading supplied input and saving the result require capabilities provided by the host.

The development link supports local authoring; it does not install the distributable plugin. The installed package uses its own files and does not depend on the link or repository governance. No marketplace catalog or installation settings are included in this change.

Verification is static only. Runtime discovery, plugin installation, and behavioral workflow execution have not been verified. Codex is the initial packaging target; portability of the instructions does not establish support for other hosts. See the [changelog](CHANGELOG.md) for changes.
