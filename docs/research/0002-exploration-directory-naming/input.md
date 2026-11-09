# Conflict-resistant naming for exploration directories

## Confirmed request

Investigate directory naming schemes for exploration projects to support choosing a scheme that avoids identifier conflicts when projects are created concurrently in one Git repository. Compare the initial candidates, examine best practices, and consider additional approaches the user may not have identified. Understand the benefits and costs of approaches that coordinate through a remote repository or another shared service and approaches that do not require such coordination. The comparison should account for meaningful topic descriptions, chronological sorting by name, and short names that are convenient to type and reference in discussions. No naming scheme has been selected.

## Context, decisions, and boundaries

- The current format is `<number>-<short-description>`, for example, `0001-exploration-input-clarification`.
- Developers may work concurrently in different branches and worktrees within one Git repository. A single developer may also create multiple worktrees, so potential identifier conflicts are not limited to collaboration between different people.
- One initial candidate retains sequential numbering: consult the remote repository for the latest number, increment it, and immediately push the new directory or branch. The user is concerned that concurrent creators could still select the same number and that resolving this could require unwanted additional checks. These are concerns to investigate, not verified findings.
- Another initial candidate combines the current date and a short description.
- Another initial candidate combines a short hash and a short description.
- Another initial candidate combines the current date, a short description, and a hash.
- These four candidates are an open starting set. Considering additional schemes is part of the requested exploration.
- There is no requirement to create directories without contacting the remote repository or another shared service. The user wants to understand the advantages and costs of both coordinated and uncoordinated approaches.
- Relative priorities among the desired naming properties have not been established. Their trade-offs are left open for exploration; the properties to compare are already identified.

## Mandatory constraints and preferences

### Preferences

- Directory names should make the exploration topic understandable.
- Sorting directories by name should reflect their order of creation.
- Names should be short and convenient to type and reference in discussions.
