---
name: exploration-input-validation
description: Check whether an exploration input Markdown document is ready for handoff. Use with supplied Markdown or an identified input file, including before confirmation or at the entry to a consuming workflow. Excludes intent clarification and research.
---

# Exploration Input Validation

Read the [validation result template](../../references/exploration/validation-result-template.md). Return its result for the current version of the supplied Markdown. Evaluate in the context supplied by the caller. For a standalone isolated check, start a new chat with the Markdown and the request to validate it. The calling workflow arranges any delegation.

1. Read the supplied Markdown text or the identified file. If the input is missing or inaccessible, return `FAIL` with the reason and what the caller needs to supply. Use available host capabilities to read the file.
2. Read the [input readiness criteria](../../references/exploration/input-readiness-criterias.md) and the [input template](../../references/exploration/input-template.md). Check the document against both. Use only the document as evidence. Do not inspect the project, follow references for missing task details, infer user confirmations, or reconstruct intent from a conversation. If required validation resources cannot be read, report the limitation as `FAIL`.
3. Return `PASS` only for a complete document that meets the criteria and template. An incomplete notice always requires `FAIL`, even when the document meets the incomplete variant's formatting rules. Report the visible blockers and which decisions or corrections are needed. For each missing, contradictory, or malformed item, name the affected section or passage where available. Report all material problems found and preserve the distinction between visible facts and unresolved decisions.

Return the result only. Leave the input and any downstream workflow to the caller.
