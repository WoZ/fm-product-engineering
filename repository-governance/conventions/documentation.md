# Documentation

## Purpose and Scope

Make repository guidance easy for agents to apply and humans to review. Read this convention when writing or restructuring documents.

## Rules

- Repository prose must use American English. Preserve exact identifiers and filenames where required by a format.
- Follow [Naming: Brand names in prose](naming.md#brand-names-in-prose) for brand references and their distinction from technical names.
- Write concise, action-oriented instructions. State concrete inputs, actions, and outcomes rather than broad aspirations.
- Use `must` for requirements, `should` for recommendations, and `may` for options.
- Convention documents should contain purpose, scope, rules, useful exceptions or examples, and verification guidance.
- Keep each normative rule in its owning convention. Link to it instead of copying it into README files or decision records.
- Use relative Markdown links for repository navigation. Label illustrative trees and examples so they cannot be mistaken for implemented packages.
- Link external technical claims to primary documentation and distinguish documented behavior from observed tests.
- Keep README files focused on purpose, navigation, and current state. Keep decision records focused on rationale.
- README titles should identify what the repository or directory provides. Introductory descriptions should explain its purpose and intended use rather than merely repeat its technical name.
- README descriptions must reflect the state they describe and link to the owning conventions for normative requirements. Use the consistency check in [Change management](change-management.md) to report discrepancies; edit related documents only when their update is part of the user's request.
- Do not rewrite historical plans, reviews, or decision records merely because current policy has changed. Distinguish historical context from current guidance.

## Verification

Resolve repository links from the containing document. Check terminology, language, standard filename spelling, example labels, and agreement with current repository state. Apply [Change management](change-management.md) for consistency checking and reporting with every change; for new filenames, apply [Naming](naming.md).
