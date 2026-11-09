# Codex Interaction Guidance

Read this reference before presenting clarification questions in Codex. The shared workflow in `SKILL.md` owns readiness, round checkpoints, confirmation, and completion; this reference only adapts their presentation.

## Choose an Available Interface

- Use a native structured question tool when it is exposed and permitted for the current turn. Read its supplied schema and restrictions; availability and supported fields depend on the host and mode. Do not assume a particular tool is always available.
- Prefer `request_user_input` when available and permitted. If the host instead exposes `request_user_input_async`, use its supported choices or free-text input and wait for the answer before taking a dependent step. A returned request identifier is not a user response.
- Let Codex render the selection interface. Do not create a custom terminal UI, simulate keyboard input, change agent settings, or switch modes to obtain a question tool.
- When a suitable tool is unavailable or disallowed, present the same question as a concise numbered text menu or a free-text prompt. Continue the workflow in chat without requiring another tool or service.

The [official Codex app-server documentation](https://learn.chatgpt.com/docs/app-server#toolrequestuserinput) describes structured user-input requests. It does not guarantee tool availability in every client or mode.

## Present Categories and Answers

Keep category selection distinct from answering a question within that category. Respect the tool's current limits on question counts, option counts, labels, and free-text support. Give options stable identifiers when the schema requires them.

For a checkpoint, show a prioritized set of relevant categories and an explicit finish-or-stop choice. Put remaining relevant directions in the short accompanying summary if they do not fit. Support a user-supplied direction through the interface's custom-answer facility or a text reply. Do not require the user to traverse every category before finishing.

For questions within the selected category, offer meaningful choices with brief implications or ask for free text. Use the interface's built-in custom-answer facility when it provides one; do not duplicate it with a synthetic option. Selecting a category does not answer its questions. Display order, recommended labels, and preselected options are not evidence of a user preference.

## Respect the Gates

Wait for an actual response at a checkpoint or confirmation. An empty response, cancellation, timeout, or automatic resolution without a user choice must not be treated as consent to continue, finish, or save. Follow higher-priority host instructions if they constrain waiting, while accurately reporting any unresolved user choice.

At `READY`, the finish choice ends deepening. Then present the complete current restatement and ask for confirmation in a separate interaction. If blockers remain, offer clarification or stopping without completion; do not label the stop choice as successful finalization.

After an answer, apply the shared workflow's reassessment rules. Keep these interaction details and round-control choices out of the saved clarified input.
