# `Topic And Context`

Use this reference when establishing the topic and relevant context for `Topic And Context`. Use the definitions and terminology rules in [the skill's terms](../SKILL.md#terms). Apply this guidance alongside the shared workflow in `SKILL.md`.

## Phase Logic

- **Topic and available context.** Use the topic, supplied materials, and relevant conversation context.
- **Initial checks.** At invocation, the first `Phase Agent Check Set` uses the available initial input. Check whether a topic is present and, when one is present, whether its meaning and the available context are sufficient for the next step.
- **Missing topic.** If no topic can be identified, use that check result to formulate a `Phase Agent Action Proposal` asking for the topic. When a topic is present, use the clarity and context check results to formulate the appropriate next interaction.
- **Targeted clarification.** When establishing the topic and context, ask only about missing information that materially affects the answer or next step.

## `Phase User Move`

The applicable `Phase User Move` categories and their handling will be defined separately.
