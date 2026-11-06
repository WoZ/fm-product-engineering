# Research on the Markdown Output of exploration-input-clarification

## Context and Goal

Study the skill `plugins/fm-research-and-analysis/skills/exploration-input-clarification`.

After the input reaches `READY` and the user provides the confirmation required by the skill, prepare a final clarified-input document for a human and the next agent, particularly for research brief creation. The skill describes the information to retain but does not prescribe its Markdown representation or exact document structure. Between runs, an agent can change formatting, section names, and content grouping.

Investigate two separate aspects of output standardization. Divide the report into Part 1 and Part 2, with separate comparisons and recommendations. Do not combine them into a final template at this stage.

## Use of the Skill Output

The primary consumer of the final Markdown document is an AI agent that will interpret and continue working with the clarified input. Human readability also matters, but unambiguous agent interpretation is the primary research criterion. The document can be saved to a file, passed by reference, or printed in full to output/stdout. Its content is the same in every case; storage and transport mechanisms are outside this research.

The research must not change workflow confirmation or completion conditions or turn clarified input into a brief, plan, or research findings.

## Part 1. Representing Information in Markdown

Investigate representation at the document level: distinguish its title from semantic categories, section boundaries, nesting relationships, and individual statements within sections.

- Compare 4–5 representations. Use the same content for a fair comparison; do not replace formatting differences with differences in the information provided.
- For each option, provide a filled comparative example, advantages, disadvantages, and risks. Show document structure, not just formatting within one section.
- Primarily assess whether the next agent can distinguish categories and preserve all material information and qualifications. Also assess human readability of raw Markdown, consistency between runs, and support for short and long explanations.
- Analyze document identification separately from content organization to avoid attributing one factor's effects to the other. Do not select particular markup levels or styles in advance. Recommend a representation and justified formatting rules.

Study the composition, names, and required status of semantic sections separately in Part 2. Section names in Part 1 examples demonstrate formatting only.

## Part 2. Section Composition and Structure

Investigate what information a human and the next agent need and how to distribute it across sections, using the skill's current requirements.

- Compare 4–5 options for section composition and grouping. Show proposed names and order, advantages, disadvantages, and risks for each option.
- Consider the confirmed request, original input and material clarifications, context, decisions, boundaries and exclusions, mandatory constraints, preferences, unconfirmed assumptions, and deferred questions.
- Do not assign a separate mandatory section to every category in advance. Justify what to combine or separate and how many nesting levels are sufficient.
- Select a recommended structure. Provide a section table specifying exact name, purpose, required status, inclusion conditions, and handling of missing information.
- Distinguish always-required sections from sections required only when corresponding material information exists. Do not allow material information to be lost because a section is labeled optional.
- Specify how to preserve distinctions between constraints and preferences, confirmed information and proposals, and brief-preparation questions and future research questions.
- Use three end-to-end synthetic examples of different classes and detail levels: a simple learning request, a request to choose an approach subject to conditions, and a detailed organizational request. Apply every grouping option to each example, not just the recommended option.
- Show concrete section content and explicitly identify missing data and omitted sections. Check for loss, duplication, and changes in meaning. Keep each example's information identical across options.
- Separately check the required status and inclusion conditions of the recommended sections against all three examples. Filled comparative options are allowed; demonstrating them does not approve or create the final template.

## Comparison Method

The main checks are preservation of all material information and distinctions between mandatory constraints and preferences, confirmed statements and unconfirmed proposals, and brief-preparation questions and future research questions. Treat agents overlooking information as a general risk to examine for every option; do not assume that a particular markup element causes it.

Distinguish current skill requirements, user preferences, analytical conclusions, and untested hypotheses. Without model trials, do not claim proven superiority in interpretation accuracy. The three end-to-end examples are required for Part 2; one identical example across all options is sufficient for Part 1.

## Expected Research Output

- A separate Part 1 comparing Markdown representations, with examples and its own recommendation.
- A separate Part 2 comparing section composition, with its own recommendation, section table, and population rules.
- An explicit distinction between current skill requirements and proposed new conventions.
- State that, after the user makes a final decision, the selected rules will be moved into a separate template file within this skill. Do not write, create, or integrate the template now; do not design its exact file location.

## Out of Scope

- Combining the two parts' recommendations into a final template. Filled comparative examples are not that template.
- Inter-agent protocols, execution statuses, checkpoints, and session recovery.
- JSON, YAML, JSONL, and serialization comparisons.
- Implementing output storage or transport.
- Template portability across skills and versioning.
- Changing the skill, its settings, or other plugin files.

Do not invent information to fill sections. Implement the selected solution in a separate subsequent step after the user reviews the findings.
