# User Decision on the Markdown Output of exploration-input-clarification

Status: approved by the user; not yet implemented in the skill.

Basis: the [research](research.md) and subsequent user decisions. This document fully specifies the target behavior for future implementation. It records the decision for `plugins/fm-research-and-analysis/skills/exploration-input-clarification`; it does not replace current skill instructions before they are separately updated.

## 1. Selected Options and Changes to the Research

- **Part 1, Option 3**, research section 1.4: “Document title and separate category headings at the next level.” Accepted: one H1 for the document, fixed H2 headings for semantic sections, and separate list items for independent statements within a section.
- **Title change:** replace `# Clarified Input` and the prefix proposed in section 1.6 with a short semantic summary of the current user request. Section 3 of this document defines how to form it.
- **Part 2, Option B**, research section 2.2: “Sections by content category,” with the inclusion rules from section 2.4 as amended by this decision.
- **Two sections removed:** “Original Input and Clarifications” and “Brief-Preparation Questions.” Remove more than their headings: do not move clarification history or a separate list of brief-preparation questions into other sections under different names. Incorporate material clarifications directly into the current request, context, and conditions.
- **Final composition:** five possible sections. “Confirmed Request” is always required; the other four are required when corresponding material information exists. The document title is not a semantic section.

This decision makes no other changes to the selected options. In particular, “Unconfirmed Assumptions and Proposals” and “Future Research Questions” retain conditional inclusion.

## 2. Purpose and Rationale

The skill output is a self-contained Markdown document representing the current, confirmed understanding of user intent. Its primary consumer is the next AI agent working on the brief; it must also be readable by a human in raw Markdown. The same content can be saved to a file, passed by reference, or printed in full to output/stdout. Transport is outside this decision.

Fixed section names and order reduce variation between runs. Heading levels identify the roles of the document and categories. Separate items preserve independent conditions and qualifications. This motivates the structure but does not prove that a particular model will never overlook information.

A meaningful H1 identifies the subject before the sections are read. The confirmed restatement inside the document remains complete; the short title does not replace it.

Removing conversation history reduces repetition and the risk of reusing interpretations that have already been corrected. It removes the history of how information arose, not its current meaning: material decisions, clarifications, context, and boundaries must appear in the appropriate sections. The next agent should not have to reconstruct intent from original messages or chat history.

Removing the brief-preparation question list preserves stage boundaries. Input clarification establishes intent; analysis of the future brief's completeness and framing belongs to the next stage. Omitting this list does not require every brief detail to be resolved now or turn those details into blockers to understanding.

The retained sections separate mandatory constraints from preferences and the accepted request from material unconfirmed statements and open research questions. Wording and content placement must make these distinctions clear; visual emphasis alone is insufficient.

## 3. Forming the H1 Title

Form the title after establishing the current confirmed request:

1. Identify the subject and what the user wants to understand, explain, or decide. Use the final understanding, including material clarifications, rather than the first message.
2. Compress this content into one short descriptive phrase. Include a material boundary if omitting it would describe a different or overly broad task.
3. Check that the title adds no technology, solution, conclusion, or goal that the user did not specify. It identifies the request rather than promising research findings.
4. Write the phrase as the sole H1 without the generic prefix `Clarified Input`. Numbering is not required. No word limit is imposed: the title should be substantially shorter than the full restatement while preserving its meaning.

For example, a request to recover photos after disk failure while excluding cloud services can use `# Backing Up Personal Photos Without Cloud Services`.

The title need not contain every constraint and preference. Record those in full in their respective sections. Revisit the title after any material correction to the request.

## 4. Document Composition and Population Rules

Present sections in the specified order. H2 names are fixed: do not replace them with synonyms between runs. Omit an unnecessary conditional section entirely, without a “not specified” placeholder. Missing data does not justify invented content or unnecessary questions solely to fill a section.

| Order | Exact H2 Name | Required Status and Content |
|---|---|---|
| 1 | Confirmed Request | Always required. A coherent restatement of intent, subject, and expected understanding or decision, including material boundaries. Incorporates the current meaning of user clarifications. A final document cannot be prepared without a confirmed restatement |
| 2 | Context, Decisions, and Boundaries | Required when material content exists. Necessary context, established decisions, subject boundaries, and exclusions. User statements are not presented as independently verified facts |
| 3 | Mandatory Constraints and Preferences | Required when at least one category exists. Preserve mandatory conditions separately from preferences, with their original force |
| 4 | Unconfirmed Assumptions and Proposals | Required when material nonblocking statements exist. Explicitly identify hypotheses and proposals as unaccepted or unverified; do not treat them as confirmed requirements |
| 5 | Future Research Questions | Required when material questions about facts, explanations, or choices have already been identified and left for research. Explain why each question or homogeneous group does not obscure current intent |

Within “Mandatory Constraints and Preferences,” use H3 headings `Mandatory Constraints` and `Preferences`. Include each subcategory only when it has content. A short document can contain only the H1 and “Confirmed Request.”

Use a paragraph for the coherent request. Use separate items for independent constraints, preferences, decisions, proposals, and questions; keep explanations and qualifications with the relevant item. Do not silently combine a mandatory condition and a preference in one item.

The primary location for a cloud-service prohibition is mandatory constraints. The primary location for excluding operating-system recovery is context and boundaries. A brief mention of a material constraint in the title or confirmed request is allowed but must preserve the meaning of its full statement.

Unconfirmed statements are not an agent's idea scratchpad. Retain only existing material statements needed to transfer the request accurately. Resolve blocking assumptions about user intent before preparing the final document; putting one in a separate section does not make the input ready.

Future research questions should not repeat the confirmed request without adding material meaning. Do not invent questions, research methods, or work plans to populate the section. Details such as data volume or organizational specifics that frame the brief without blocking understanding must not be relabeled as research questions.

## 5. Excluded Content

The final document need not retain original messages, question-and-answer history, previous interpretations, or a mandatory reference to the original input for reconstructing history. Their material current meaning must already appear in the accepted sections. If a particular user-supplied resource is itself the subject of the request, a necessary reference may remain in context; this does not restore the removed history section.

Do not generate or retain a separate list of brief-preparation questions. The next stage determines the details needed for the brief. Do not remove an existing user decision or constraint merely because it affects the brief: preserve its original meaning in context or conditions.

The output contains no execution log, internal analysis questionnaire, brief, research plan, or research findings.

## 6. Filled Example of the Accepted Format

This example is synthetic. Assume that the request and boundaries are confirmed and the remaining proposal is explicitly unaccepted. It demonstrates the approved decision; it is not a separate template file.

```markdown
# Backing Up Personal Photos Without Cloud Services

## Confirmed Request

The user wants to understand how to back up personal photos
from a home computer so they can be recovered after disk failure.
Cloud services are excluded; the choice of a local approach remains open.

## Context, Decisions, and Boundaries

- Operating-system recovery is outside the request.

## Mandatory Constraints and Preferences

### Mandatory Constraints

- Cloud services are prohibited.

### Preferences

- Prefer using the existing external drive;
  this is not mandatory.

## Unconfirmed Assumptions and Proposals

- The earlier proposal to evaluate an additional copy at another location
  is unconfirmed and is not an accepted requirement.

## Future Research Questions

- Which local approaches suit backup and recovery?
  This is left for research because the user wants to understand
  organizational approaches and has not selected a specific solution.
```

## 7. Instructions for Future Implementation

In a separate implementation task, put the accepted format and population rules in a template file within this skill and reference it explicitly from `SKILL.md`. The installed package must contain all necessary instructions; it must not depend on this document in the research directory. A shared template for other skills and template versioning are outside scope.

Before implementation, the following discrepancies exist with the current [SKILL.md](../../../plugins/fm-research-and-analysis/skills/exploration-input-clarification/SKILL.md):

| Current Location | Discrepancy | Required Alignment During Implementation |
|---|---|---|
| Section 5, original input or accessible reference item | Retaining a source is currently required, whereas the accepted decision does not require transferring original input and history | Replace the source-transfer obligation with self-contained current content and preservation of the material meaning of clarifications |
| Section 5, open questions item | Currently retains brief-preparation and research questions; the decision retains only the latter | Remove the obligation to retain a separate brief-question list; retain rules for material research questions |
| Section 3, deferring gaps while preserving them for the next stage; Section 4, presenting deferred questions | These instructions must not be interpreted as requiring the deleted list in the final document | Distinguish recognizing a nonblocking gap during clarification from including it in the final artifact. Do not relocate brief questions or force the user to answer them now |

These changes affect instruction content, not just formatting. Preserve readiness, confirmation of the current restatement, successful saving, and stopping before brief creation. Save-failure handling and the prohibition on unauthorized overwrites also remain unchanged. Transferring Markdown through output does not itself remove the existing saving condition for workflow completion.

The current task records the decision only: `SKILL.md`, the template, settings, and plugin version are unchanged. Subsequent implementation must align affected documentation and compatibility with repository rules; creating this document does not perform that work.

## 8. Acceptance Criteria for Future Output

- The next agent can understand the document without chat history: material clarifications, decisions, and conditions are retained directly in its content.
- Exactly one H1 provides a short semantic summary of the confirmed request without a generic prefix.
- H2 headings match the five accepted names and order. “Confirmed Request” is always present; the other sections and two condition subcategories appear only when material content exists.
- There is no clarification history, disguised original-input section, or brief-preparation question list. Removing them must not lose material current conditions.
- Preferences do not become prohibitions, proposals do not become decisions, and user hypotheses do not become established facts. Blocking questions are not hidden in conditional sections.
- A simple learning request may contain only the title and confirmed request. A detailed request retains every material category without invented filler.
- Check both normal Markdown saving and preservation of the same meaning when transferring content to the next agent. Guarantees about a particular model's interpretation require separate behavioral testing.

This document and the related research were originally written in Russian at the user's request and subsequently translated into American English at the user's direction. The former language exception to [AGENTS.md](../../../AGENTS.md) and [Documentation](../../../repository-governance/conventions/documentation.md) no longer applies to this translation. This document records a specific skill decision, not a new repository-wide policy.
