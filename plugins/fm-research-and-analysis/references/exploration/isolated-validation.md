# Isolated Exploration Input Validation

Use this procedure when the current conversation contains clarification history or other task evidence besides the Markdown, or when the calling workflow requires a separate check before confirmation.

## Delegate the Current Markdown

1. Start a new agent without the current conversation history. Supply the exact Markdown as data and the resolved path to the installed [exploration-input-validation skill](../../skills/exploration-input-validation/SKILL.md). Ask the agent to read those instructions, use only the supplied Markdown as evidence, and return the result in the [validation result format](validation-result-template.md). Omit dialogue summaries, prior reports, explanations of the task, and expected results from the delegation message.
2. Wait for the result. Use only the returned report in the main conversation. Accept it for the exact Markdown submitted. If the Markdown changes before the result is used, check the new version in a fresh context.
3. If the isolated run cannot start or does not yield a usable report, follow the new-chat handoff below.

### Codex

Use the available subagent tool and explicitly select no parent history. Use `fork_turns: "none"` when the tool exposes `fork_turns`, or `fork_context: false` when it exposes `fork_context`. Wait for its final report. If the tool cannot start an agent without inheriting history, use the new-chat handoff.

### Claude Code

Use `Agent` to start a fresh ordinary subagent in the foreground and wait for its final report. Supply the Markdown and validator path in the task. Use an ordinary subagent rather than a fork or a resumed agent, which can contain prior conversation history.

## New-Chat Handoff

Tell the user explicitly when separate agent launch is disabled in the current client. If it is unavailable for another or unknown reason, say that it is unavailable and state the cause if known. If an agent started but the run failed, identify that failure instead of treating it as a document verdict.

Show the exact Markdown as a draft for transfer. Ask the user to open a new chat, run `exploration-input-validation` there with this Markdown alone, and return its short report with confirmation that this exact version was checked. Wait before requesting confirmation or proceeding with the consuming workflow. Resume only after the user returns a report for the pending version. Apply `FAIL` as a document result and request a new check if the Markdown changes. A previous report or a check in the current conversation cannot complete this handoff.
