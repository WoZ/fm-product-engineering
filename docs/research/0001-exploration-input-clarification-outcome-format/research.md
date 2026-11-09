# Research on the Markdown Output of exploration-input-clarification

Date: November 6, 2026. Basis: the [updated task](input.md) and current [SKILL.md](../../../plugins/fm-research-and-analysis/skills/exploration-input-clarification/SKILL.md).

The report contains two separate investigations. Part 1 selects a Markdown representation; Part 2 selects semantic section composition and grouping. Part 1 examines four structural options and, separately, document titles; Part 2 examines five groupings. Recommendations are separate. Filled examples support comparison; no final template is assembled.

## Basis and Comparison Method

The current skill already requires retaining the confirmed restatement, original input or an accessible reference, material clarifications, stated decisions and boundaries, constraints and preferences, material unconfirmed proposals, and deferred questions. Brief-preparation and future research questions are distinguished, with explanations of why they may remain open. Content must not become a brief, plan, or research findings. These are requirements from skill Section 5, not new rules introduced by this report.

Skill Section 2 explicitly says that internal analysis criteria are not required artifact fields. Therefore, copying the entire internal questionnaire into the document structure requires justification.

The exact headings, section order, Markdown elements, and empty-section omission rules below are research proposals. They have not yet been approved or implemented.

Technical basis: [CommonMark headings](https://spec.commonmark.org/0.31.2/#atx-headings), [lists](https://spec.commonmark.org/0.31.2/#lists), [block quotes](https://spec.commonmark.org/0.31.2/#block-quotes), and [links](https://spec.commonmark.org/0.31.2/#links) are basic markup elements. Pipe tables are a [GFM extension](https://github.github.com/gfm/#tables-extension-); identical rendering cannot be assumed for every Markdown renderer. Standards define syntax, not the meaning of clarified-input sections.

This comparison is qualitative: it analyzes preservation of meaning and representational consistency. No model experiments or extraction-accuracy measurements were performed. Convenience and risk assessments are analytical conclusions, not established quality metrics for a particular agent.

## Part 1. Representing Information in Markdown

### 1.1. Criteria and Identical Content

The primary consumer is an AI agent reading raw Markdown. Assess explicit category boundaries, preservation of every material statement and its force, and distinction between document titles and categories. Human readability is secondary. Examine omission risk for every option; without testing, a particular heading level cannot be claimed to automatically receive less model attention.

All four options use the same information:

- Goal: understand how to organize backups of personal photos from a home computer for recovery after disk failure.
- Mandatory constraints: cloud services are excluded; buying a new drive is allowed only if necessary.
- Preferences: preferably use the existing external drive; preferably avoid paid subscriptions. Neither preference is mandatory.

This is a demonstration fragment, not complete clarified input. Two entries in each condition category show how to keep independent statements separate. Example categories do not predetermine Part 2 sections. A table was excluded as an output representation at the user's preference; comparison tables in the report remain.

### 1.2. Option 1: Title and Bulleted Categories Without Separate Headings

```markdown
# Clarified Input

- Goal: understand how to organize backups of personal photos
  from a home computer for recovery after disk failure.
- Mandatory constraints:
  - Cloud services are excluded.
  - Buying a new drive is allowed only if necessary.
- Preferences, not mandatory conditions:
  - Prefer using the existing external drive.
  - Prefer avoiding paid subscriptions.
```

**Advantages:** compact; categories are explicitly named; separate items preserve independent conditions.

**Disadvantages:** categories and data use the same list element; losing indentation makes their relationship less explicit.

**Agent risk:** treating a category label as another condition or losing a nested item's parent. This control option tests the benefit of separate headings without changing content.

### 1.3. Option 2: Title and Categories as Equal-Level Headings

```markdown
# Clarified Input

# Goal

Understand how to organize backups of personal photos
from a home computer for recovery after disk failure.

# Mandatory Constraints

- Cloud services are excluded.
- Buying a new drive is allowed only if necessary.

# Preferences, Not Mandatory Conditions

- Prefer using the existing external drive.
- Prefer avoiding paid subscriptions.
```

**Advantages:** each category has an explicit boundary; statements inside it are separated; no deep nesting.

**Disadvantages:** the document title and categories share a structural level. Distinguishing their roles requires another convention, such as “the first heading is the title.”

**Agent risk:** ambiguity about the first heading when combining documents or extracting a fragment. Multiple H1 headings are syntactically valid; this is a structural assessment, not a claim that Markdown prohibits them.

### 1.4. Option 3: Document Title and Separate Category Headings at the Next Level

```markdown
# Clarified Input

## Goal

Understand how to organize backups of personal photos
from a home computer for recovery after disk failure.

## Mandatory Constraints

- Cloud services are excluded.
- Buying a new drive is allowed only if necessary.

## Preferences, Not Mandatory Conditions

- Prefer using the existing external drive.
- Prefer avoiding paid subscriptions.
```

**Advantages:** distinguishes the document from its categories; peer categories share a level; multiple conditions are not merged into a paragraph. The exact heading name identifies a category.

**Disadvantages:** requires a fixed vocabulary of names; heading synonyms between runs preserve variability. Highly detailed documents may need another level.

**Agent risk:** headings do not prevent skipping an item or confusing a preference with a constraint. Explicit semantic labels remain necessary, and factual accuracy needs separate checks.

### 1.5. Option 4: Title, Group Headings, and Nested Category Headings

```markdown
# Clarified Input

## Request

### Goal

Understand how to organize backups of personal photos
from a home computer for recovery after disk failure.

## Conditions

### Mandatory Constraints

- Cloud services are excluded.
- Buying a new drive is allowed only if necessary.

### Preferences, Not Mandatory Conditions

- Prefer using the existing external drive.
- Prefer avoiding paid subscriptions.
```

**Advantages:** distinguishes groups from categories; suits long documents that genuinely need groups; data retains its labels.

**Disadvantages:** more structural headings; groups add little information in a short example. Fragment interpretation may depend on retaining the parent heading.

**Agent risk:** losing parent context during extraction. H3 content must not be considered less binding: meaning, not heading depth, defines a constraint's force. Check general omission risks just as for other options.

### 1.6. Separate Factor: Document Title

To avoid confounding effects, sections 1.2–1.5 use the same title. Below, only the title changes; Option 3 structure and all content remain unchanged.

| Title | Benefit | Limitation and Risk |
|---|---|---|
| `# Clarified Input` | Stable document-type label | The topic must be read from content; multiple documents look identical in a list |
| `# Backing Up Photos` | Immediately identifies the topic | Does not identify whether this is clarified input, a brief, or completed research |
| `# Research 002: Backing Up Photos` | Identifies number and topic | May imply research findings; needs a source for the number that the format does not establish |

**Proposal:** use a stable document-type label with a topical addition, such as `# Clarified Input: Backing Up Photos`. Do not require numbering without an existing user numbering scheme; a supplied number may appear in the title. This is this research's recommendation, not a universal comparison-method requirement.

### 1.7. Comparison and Recommendation for Part 1

| Option | Category Boundaries | Distinguishing Title from Categories | Fragment Independence | Main Risk |
|---|---|---|---|---|
| 1. Categories as a list | Labels and indentation | Title is distinguished | Depends on indentation | Losing an item's parent |
| 2. Equal-level headings | Explicit | Requires another convention | Names distinguish categories | Ambiguous role of the first heading |
| 3. Title and category headings | Explicit | Defined by levels | High if the category heading is retained | Variable names and skipped items |
| 4. Groups and nested categories | Explicit, hierarchical | Defined by levels | May need the parent heading | Excessive nesting and lost context |

**Recommendation: Option 3.** One H1 identifies the document; peer H2 headings identify categories. Independent statements inside categories use list items; a coherent goal statement may remain a paragraph. Nested H3 headings are allowed only for useful semantic distinctions, not to indicate lower importance.

The rationale is explicit roles and few structural conventions. This is a qualitative conclusion, not proven superiority in a particular model's accuracy. One H1 or additional headings alone cannot be promised to prevent information loss.

Additional rules: fix category names after the Part 2 decision; do not substitute synonyms between runs; retain qualifications such as “preferably” and “unconfirmed”; do not duplicate a condition with different force. Distinguish quotations from paraphrases; provide source materials through accessible references or material text. Content must be readable in raw Markdown without hidden comments or required rendering.

## Part 2. Section Composition and Structure

### 2.1. Information to Preserve Regardless of Grouping

Define information obligations before section boundaries. The current skill requires five content groups:

1. A confirmed restatement of intent and expected understanding or decision.
2. Original input or an accessible source and material user clarifications.
3. Stated decisions, boundaries, exclusions, mandatory constraints, and preferences, preserving their distinctions.
4. Material unconfirmed assumptions or proposals, if any remain.
5. Material open questions distinguished as brief-preparation or research questions, explaining why deferral is acceptable.

Retain material context and motivation wherever needed for understanding. Not every request needs separate “business problem,” “decision,” or “technology” fields: research may concern learning or explaining a phenomenon.

### 2.2. Five Grouping Options

The names below are candidates for discussion. Each description is followed by a concrete population using the same backup example from 2.4, where cloud services are prohibited. Bracketed omission notes explain the demonstration and should not appear in final input. These are comparative examples, not an accepted template.

#### Option A. Compact Three-Section Document

1. **Confirmed Request** — restatement, context, decisions, boundaries, constraints, and preferences with explicit internal labels.
2. **Original Input and Clarifications** — accessible sources and material request changes.
3. **Open Statements** — separately labeled unconfirmed proposals and questions for the next two stages.

**Concrete backup distribution (Example 2 from section 2.4):**

```markdown
## Confirmed Request

Request: Understand how to organize backups of personal photos from a home computer for recovery after disk failure. Boundaries: Operating-system recovery is outside the request. Mandatory constraint: Cloud services are prohibited. Preference: Prefer using the existing external drive; this is not mandatory.

## Original Input and Clarifications

Original statement: “I want to understand backup.” Clarifications: personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.

## Open Statements

Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement. Brief preparation: What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail. Future research: Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.
```

**Advantages:** few headings; short requests remain small; all skill requirements fit without a separate section for each category.

**Disadvantages:** semantic categories must be reconstructed from labels in large sections. “Open Statements” combines information with different purposes.

**Risks:** an unconfirmed proposal becomes a research question or condition; a long first section blurs constraints and preferences.

**Choose:** for consistently short requests. For a general-purpose skill, it depends too heavily on careful internal labels.

#### Option B. Sections by Content Category

1. **Confirmed Request**.
2. **Original Input and Clarifications**.
3. **Context, Decisions, and Boundaries**.
4. **Mandatory Constraints and Preferences** — with separate subcategories.
5. **Unconfirmed Assumptions and Proposals**.
6. **Brief-Preparation Questions**.
7. **Future Research Questions**.

**Concrete backup distribution (Example 2 from section 2.4):**

```markdown
## Confirmed Request

Understand how to organize backups of personal photos from a home computer for recovery after disk failure.

## Original Input and Clarifications

Original statement: “I want to understand backup.” Clarifications: personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.

## Context, Decisions, and Boundaries

Boundaries: Operating-system recovery is outside the request.

## Mandatory Constraints and Preferences

Mandatory constraint: Cloud services are prohibited. Preference: Prefer using the existing external drive; this is not mandatory.

## Unconfirmed Assumptions and Proposals

Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement.

## Brief-Preparation Questions

What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail.

## Future Research Questions

Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.
```

**Advantages:** categories directly reflect skill content; the next agent sees what is a task condition versus an unaccepted proposal; analysis criteria need not become a questionnaire.

**Disadvantages:** small requests rarely need seven populated sections. Rules for distributing context, boundaries, and requirements are needed to prevent duplication.

**Risks:** filling absent categories mechanically; a short constraint restatement diverging from the full record. Conditional inclusion and one primary location per statement address these risks.

**Choose:** as this skill's general structure with clear required-status rules. Recommended.

#### Option C. Maximally Detailed Separate Sections

Example composition: **Confirmed Request**, **Original Input**, **User Clarifications**, **Context**, **Decisions**, **Boundaries**, **Exclusions**, **Mandatory Constraints**, **Preferences**, **Unconfirmed Assumptions and Proposals**, **Brief-Preparation Questions**, **Future Research Questions**.

**Concrete backup distribution (Example 2 from section 2.4):**

```markdown
## Confirmed Request

Understand how to organize backups of personal photos from a home computer for recovery after disk failure.

## Original Input

Original statement: “I want to understand backup.”

## User Clarifications

Personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.

## Context

[No data in this example; omit the section.]

## Decisions

[No data in this example; omit the section.]

## Boundaries

Understand how to organize backups of personal photos from a home computer for recovery after disk failure.

## Exclusions

Operating-system recovery is outside the request.

## Mandatory Constraints

Cloud services are prohibited.

## Preferences

Prefer using the existing external drive; this is not mandatory.

## Unconfirmed Assumptions and Proposals

Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement.

## Brief-Preparation Questions

What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail.

## Future Research Questions

Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.
```

**Advantages:** explicit locations for every category; easy to check a particular information type; little internal classification required.

**Disadvantages:** twelve possible sections; fine-grained categories often overlap; headings may outnumber useful statements. Section count does not establish semantic completeness.

**Risks:** repeating the cloud prohibition under exclusions and constraints, or inventing a “decision” or “context” to fill empty sections.

**Choose:** when real long requests regularly contain all these independent categories. This detail is premature for the current general-purpose skill.

#### Option D. Grouping by Confirmation Status

1. **Confirmed Information** — request, stated context, decisions, and conditions with internal labels.
2. **Unconfirmed Statements** — assumptions and proposals.
3. **Deferred Questions** — two subcategories by subsequent stage.
4. **Sources and Clarifications** — content provenance.

**Concrete backup distribution (Example 2 from section 2.4):**

```markdown
## Confirmed Information

Request: Understand how to organize backups of personal photos from a home computer for recovery after disk failure. Boundaries: Operating-system recovery is outside the request. Mandatory constraint: Cloud services are prohibited. Preference: Prefer using the existing external drive; this is not mandatory.

## Unconfirmed Statements

Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement.

## Deferred Questions

Brief preparation: What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail. Future research: Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.

## Sources and Clarifications

Original statement: “I want to understand backup.” Clarifications: personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.
```

**Advantages:** agreement status is immediately visible; proposals are separate from the accepted request; few major sections.

**Disadvantages:** “confirmed information” hides different content types. Confirmed user intent is different from a proven external fact.

**Risks:** a user hypothesis starts to look like an established fact; constraints and preferences are again combined within one section.

**Choose:** when the document primarily supports agreement on proposals. Transferring input to a brief needs more internal distinctions, reducing the compactness benefit.

#### Option E. Grouping by Internal Analysis Criteria

Example composition: **Intent**, **Problem or Need**, **Expected Understanding or Decision**, **Context**, **Boundaries**, **Constraints and Preferences**, **Ambiguities**, **Contradictions**, **Assumptions**, **Research Suitability**; original input and deferred questions need additional locations.

**Concrete backup distribution (Example 2 from section 2.4):**

```markdown
## Intent

Understand how to organize backups of personal photos from a home computer for recovery after disk failure.

## Problem or Need

[No data in this example; omit the section.]

## Expected Understanding or Decision

Understand how to organize backups of personal photos from a home computer for recovery after disk failure.

## Context

[No data in this example; omit the section.]

## Boundaries

Boundaries: Operating-system recovery is outside the request.

## Constraints and Preferences

Mandatory constraint: Cloud services are prohibited. Preference: Prefer using the existing external drive; this is not mandatory.

## Ambiguities

No user information justifies a separate section; do not add an internal assessment.

## Contradictions

No user information justifies a separate section; do not add an internal assessment.

## Assumptions

Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement.

## Research Suitability

This is the executor's internal assessment, not user content.

## Addition: Original Input and Clarifications

Original statement: “I want to understand backup.” Clarifications: personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.

## Addition: Deferred Questions

Brief preparation: What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail. Future research: Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.
```

**Advantages:** resembles an analysis checklist; convenient for inspecting which aspects the executor checked.

**Disadvantages:** describes the analysis performed rather than the clarification result; repeats the request; the criteria do not cover all required input transfer.

**Risks:** inventing a problem when the user only wants to learn about a phenomenon, or presenting internal assessments as user requirements. Making the criteria mandatory sections conflicts with the explicit instruction in skill Section 2.

**Choose:** as an internal executor check, not as final input structure. This option tests the common temptation to reuse an existing criteria list; it cannot be recommended.

### 2.3. Comparison and Recommendation for Part 2

| Option | Possible Main Sections | Category Distinction | Duplication Risk | Fit for the Current Skill |
|---|---|---|---|---|
| A. Compact | 3 | Depends on internal labels | Moderate | Good for simple cases, weaker for complex ones |
| B. By content | 7 | High with distribution rules | Manageable | Recommended |
| C. Detailed | 12 | High | High due to overlaps | Excessive without a demonstrated need |
| D. By confirmation status | 4 | Good for agreement, weaker for condition types | Moderate | Risks treating hypotheses as facts |
| E. By analysis criteria | 10 plus input-transfer sections | Reflects executor work | High | Conflicts with the criteria's role when made required fields |

**Recommendation: Option B, with seven possible sections, five included conditionally.** Two sections are always needed: the confirmed request and original input with material clarifications. The others are required only when corresponding material information exists. A simple request may have two semantic sections; seven is not a quota.

The three examples in 2.4 refine this choice: A and D retain data only with explicit internal labels; C fragments short requests and repeats them under boundaries; E duplicates intent and expected understanding and needs extra input-transfer locations. B gives material distinctions their own locations while leaving only two sections for a short request. In the detailed organizational example, the user's hypothesis remains unconfirmed even though the reported observation appears in context. Recommendation B therefore follows the comparison, not an assumed ideal heading count.

The selected grouping's semantic boundaries are these: the subject and established decisions describe what the user is investigating; mandatory constraints and preferences describe its conditions; unconfirmed proposals do not become part of the accepted request; the two open-question types retain their next-stage purposes.

### 2.4. Proposed Sections and Inclusion Rules

The exact names below were originally proposed in Russian for user review and are translated consistently here. They do not change current skill instructions. The overall document title is not a semantic section.

| Order | Exact Name | Purpose and Content | Required Status | If Data Is Missing |
|---|---|---|---|---|
| 1 | Confirmed Request | Coherent statement of intent, subject, and expected understanding or decision; material boundaries needed for accurate reading | Always | Without an accepted restatement, final input cannot yet be prepared |
| 2 | Original Input and Clarifications | Original text or accessible reference; material user answers, corrections, and changes | Always | If there were no clarifications, retain the original input or reference; do not invent a dialogue |
| 3 | Context, Decisions, and Boundaries | Material stated context, established decisions, subject boundaries, and exclusions not recorded as conditions | When such material information exists | Omit; do not invent a problem or decision |
| 4 | Mandatory Constraints and Preferences | Separate mandatory conditions and preferences, preserving their force | When either category exists | Omit the section if both are absent; omit only the missing subcategory otherwise |
| 5 | Unconfirmed Assumptions and Proposals | Material remaining assumptions and proposals, explicitly marked as unaccepted | When present | Omit; absence does not turn agent guesses into confirmed information |
| 6 | Brief-Preparation Questions | Material questions framing the future brief; explain why they do not obscure current intent | When present | Omit; do not generate an extra questionnaire |
| 7 | Future Research Questions | Material open factual questions and choices the user left for research; explain why deferral is acceptable | When present | Omit; do not create a research plan or expanded task list |

Section 4 proposes fixed subcategories **Mandatory Constraints** and **Preferences**, each included only when populated. Persistent empty subcategories labeled “not specified” add little value and should not trigger more questions.

Section 3 does not need permanent subheadings for each category. Explicit labels such as “Context,” “User decision,” “Boundaries,” or “Exclusion” suffice when multiple types exist. A prohibition defining approach conditions belongs in Section 4, such as excluding cloud services. Excluding subject matter, such as operating-system recovery, belongs in Section 3. Neither statement needs repetition in both sections.

A precise section name does not make every statement a proven fact. Transfer user-reported context as their information, preserve qualifications on their hypotheses, and mark agent proposals as unconfirmed. Section 5 is only for nonblocking statements: it cannot hide unknown intent and make input ready.

In Sections 6 and 7, attach the deferral explanation to the question or a homogeneous group sharing a reason. “Clarify later” without explanation is insufficient. Do not expand the future research program solely to fill a section.

#### 2.4.1. Three End-to-End Examples and Reading Order

All examples are synthetic. An absent category means corresponding data is missing in that example, not permission to discard existing information. Each grouping below shows concrete content for every section. Repetition in C and E is intentionally visible as a grouping disadvantage. Extra sections in E are explicitly labeled additions: the original ten criteria do not meet input-transfer requirements.

#### 2.4.2. Example 1: Learning Request: Seasons on Mars

**Source Information for All Five Options:**

- Request: Understand why seasons change on Mars.
- Source and clarifications: Original statement: “I want to understand why seasons change on Mars.” There were no material clarifications; restatement confirmed.

##### Example 1 / Option A

- **Confirmed Request**: Request: Understand why seasons change on Mars.
- **Original Input and Clarifications**: Original statement: “I want to understand why seasons change on Mars.” There were no material clarifications; restatement confirmed.
- **Open Statements**: No corresponding information in this example; omit the section.

##### Example 1 / Option B

- **Confirmed Request**: Understand why seasons change on Mars.
- **Original Input and Clarifications**: Original statement: “I want to understand why seasons change on Mars.” There were no material clarifications; restatement confirmed.
- **Context, Decisions, and Boundaries**: No corresponding information in this example; omit the section.
- **Mandatory Constraints and Preferences**: No corresponding information in this example; omit the section.
- **Unconfirmed Assumptions and Proposals**: No corresponding information in this example; omit the section.
- **Brief-Preparation Questions**: No corresponding information in this example; omit the section.
- **Future Research Questions**: No corresponding information in this example; omit the section.

##### Example 1 / Option C

- **Confirmed Request**: Understand why seasons change on Mars.
- **Original Input**: Original statement: “I want to understand why seasons change on Mars.” There were no material clarifications; restatement confirmed.
- **User Clarifications**: No corresponding information in this example; omit the section.
- **Context**: No corresponding information in this example; omit the section.
- **Decisions**: No corresponding information in this example; omit the section.
- **Boundaries**: Understand why seasons change on Mars.
- **Exclusions**: No corresponding information in this example; omit the section.
- **Mandatory Constraints**: No corresponding information in this example; omit the section.
- **Preferences**: No corresponding information in this example; omit the section.
- **Unconfirmed Assumptions and Proposals**: No corresponding information in this example; omit the section.
- **Brief-Preparation Questions**: No corresponding information in this example; omit the section.
- **Future Research Questions**: No corresponding information in this example; omit the section.

##### Example 1 / Option D

- **Confirmed Information**: Request: Understand why seasons change on Mars.
- **Unconfirmed Statements**: No corresponding information in this example; omit the section.
- **Deferred Questions**: No corresponding information in this example; omit the section.
- **Sources and Clarifications**: Original statement: “I want to understand why seasons change on Mars.” There were no material clarifications; restatement confirmed.

##### Example 1 / Option E

- **Intent**: Understand why seasons change on Mars.
- **Problem or Need**: No corresponding information in this example; omit the section.
- **Expected Understanding or Decision**: Understand why seasons change on Mars.
- **Context**: No corresponding information in this example; omit the section.
- **Boundaries**: No corresponding information in this example; omit the section.
- **Constraints and Preferences**: No corresponding information in this example; omit the section.
- **Ambiguities**: No user information justifies a separate section; do not add an internal assessment.
- **Contradictions**: No user information justifies a separate section; do not add an internal assessment.
- **Assumptions**: No corresponding information in this example; omit the section.
- **Research Suitability**: This is the executor's internal assessment, not user content.
- **Addition: Original Input and Clarifications**: Original statement: “I want to understand why seasons change on Mars.” There were no material clarifications; restatement confirmed.
- **Addition: Deferred Questions**: No corresponding information in this example; omit the section.

**Check of recommended Structure B:** only the confirmed request and original input are needed. Omit the other five sections. Do not copy the seasons question into a research program again.

#### 2.4.3. Example 2: Choosing an Approach: Photo Backup

**Source Information for All Five Options:**

- Request: Understand how to organize backups of personal photos from a home computer for recovery after disk failure.
- Source and clarifications: Original statement: “I want to understand backup.” Clarifications: personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.
- Boundaries: Operating-system recovery is outside the request.
- Mandatory constraint: Cloud services are prohibited.
- Preference: Prefer using the existing external drive; this is not mandatory.
- Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement.
- Brief preparation: What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail.
- Future research: Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.

##### Example 2 / Option A

- **Confirmed Request**: Request: Understand how to organize backups of personal photos from a home computer for recovery after disk failure. Boundaries: Operating-system recovery is outside the request. Mandatory constraint: Cloud services are prohibited. Preference: Prefer using the existing external drive; this is not mandatory.
- **Original Input and Clarifications**: Original statement: “I want to understand backup.” Clarifications: personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.
- **Open Statements**: Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement. Brief preparation: What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail. Future research: Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.

##### Example 2 / Option B

- **Confirmed Request**: Understand how to organize backups of personal photos from a home computer for recovery after disk failure.
- **Original Input and Clarifications**: Original statement: “I want to understand backup.” Clarifications: personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.
- **Context, Decisions, and Boundaries**: Boundaries: Operating-system recovery is outside the request.
- **Mandatory Constraints and Preferences**: Mandatory constraint: Cloud services are prohibited. Preference: Prefer using the existing external drive; this is not mandatory.
- **Unconfirmed Assumptions and Proposals**: Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement.
- **Brief-Preparation Questions**: What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail.
- **Future Research Questions**: Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.

##### Example 2 / Option C

- **Confirmed Request**: Understand how to organize backups of personal photos from a home computer for recovery after disk failure.
- **Original Input**: Original statement: “I want to understand backup.”
- **User Clarifications**: Personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.
- **Context**: No corresponding information in this example; omit the section.
- **Decisions**: No corresponding information in this example; omit the section.
- **Boundaries**: Understand how to organize backups of personal photos from a home computer for recovery after disk failure.
- **Exclusions**: Operating-system recovery is outside the request.
- **Mandatory Constraints**: Cloud services are prohibited.
- **Preferences**: Prefer using the existing external drive; this is not mandatory.
- **Unconfirmed Assumptions and Proposals**: Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement.
- **Brief-Preparation Questions**: What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail.
- **Future Research Questions**: Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.

##### Example 2 / Option D

- **Confirmed Information**: Request: Understand how to organize backups of personal photos from a home computer for recovery after disk failure. Boundaries: Operating-system recovery is outside the request. Mandatory constraint: Cloud services are prohibited. Preference: Prefer using the existing external drive; this is not mandatory.
- **Unconfirmed Statements**: Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement.
- **Deferred Questions**: Brief preparation: What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail. Future research: Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.
- **Sources and Clarifications**: Original statement: “I want to understand backup.” Clarifications: personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.

##### Example 2 / Option E

- **Intent**: Understand how to organize backups of personal photos from a home computer for recovery after disk failure.
- **Problem or Need**: No corresponding information in this example; omit the section.
- **Expected Understanding or Decision**: Understand how to organize backups of personal photos from a home computer for recovery after disk failure.
- **Context**: No corresponding information in this example; omit the section.
- **Boundaries**: Boundaries: Operating-system recovery is outside the request.
- **Constraints and Preferences**: Mandatory constraint: Cloud services are prohibited. Preference: Prefer using the existing external drive; this is not mandatory.
- **Ambiguities**: No user information justifies a separate section; do not add an internal assessment.
- **Contradictions**: No user information justifies a separate section; do not add an internal assessment.
- **Assumptions**: Unconfirmed proposal: The agent proposal to evaluate an additional copy at another location is unconfirmed and is not an accepted requirement.
- **Research Suitability**: This is the executor's internal assessment, not user content.
- **Addition: Original Input and Clarifications**: Original statement: “I want to understand backup.” Clarifications: personal photos, a home computer, recovery after disk failure; cloud excluded; existing drive preferred; system recovery excluded. Restatement confirmed.
- **Addition: Deferred Questions**: Brief preparation: What is the photo volume? Deferred to brief preparation: the subject, recovery goal, and exclusions are clear without this detail. Future research: Which local approaches suit backup and recovery? Left for research: the user wants to investigate approaches and has not selected a solution.

**Check of recommended Structure B:** all seven sections are used; the cloud prohibition and drive preference remain distinct. The additional-copy proposal did not become a requirement; photo volume and approach selection are deferred for different reasons.

#### 2.4.4. Example 3: Organizational Request: Support Shift Handoffs

**Source Information for All Five Options:**

- Request: Understand the causes of information loss during support shift handoffs and possible improvements within the selected tracking system and current staffing.
- Source and clarifications: Original statement: “I want to understand why tickets get lost during shift handoffs.” Clarifications: support handoffs are the subject; the tracking system is already selected, changing it and increasing staffing are prohibited; existing tools are preferred. Goal and boundaries confirmed.
- Context: The user reports that tickets get lost during shift handoffs; this observation has not been independently verified.
- User decision: The user has already selected the tracking system; reconsidering that choice was not requested.
- Boundaries: Investigate handoff causes and possible improvements; system replacement and staffing expansion are excluded.
- Mandatory constraint: Do not change the selected tracking system or increase staffing.
- Preference: Prefer existing tools; additional tools are not prohibited if they meet the constraints.
- Unconfirmed hypothesis: User hypothesis: information is lost because of verbal handoffs. This is not an established cause.
- Unconfirmed proposal: The agent proposal to evaluate a handoff checklist is unconfirmed and is not a selected solution.
- Brief preparation: How are shift roles and hours distributed? Deferred to the brief: the goal, process, and mandatory boundaries are already clear.
- Future research: Which causes of information loss and improvement measures need to be established? Left for research: the causes and suitable measures are not yet known.

##### Example 3 / Option A

- **Confirmed Request**: Request: Understand the causes of information loss during support shift handoffs and possible improvements within the selected tracking system and current staffing. Context: The user reports that tickets get lost during shift handoffs; this observation has not been independently verified. User decision: The user has already selected the tracking system; reconsidering that choice was not requested. Boundaries: Investigate handoff causes and possible improvements; system replacement and staffing expansion are excluded. Mandatory constraint: Do not change the selected tracking system or increase staffing. Preference: Prefer existing tools; additional tools are not prohibited if they meet the constraints.
- **Original Input and Clarifications**: Original statement: “I want to understand why tickets get lost during shift handoffs.” Clarifications: support handoffs are the subject; the tracking system is already selected, changing it and increasing staffing are prohibited; existing tools are preferred. Goal and boundaries confirmed.
- **Open Statements**: Unconfirmed hypothesis: User hypothesis: information is lost because of verbal handoffs. This is not an established cause. Unconfirmed proposal: The agent proposal to evaluate a handoff checklist is unconfirmed and is not a selected solution. Brief preparation: How are shift roles and hours distributed? Deferred to the brief: the goal, process, and mandatory boundaries are already clear. Future research: Which causes of information loss and improvement measures need to be established? Left for research: the causes and suitable measures are not yet known.

##### Example 3 / Option B

- **Confirmed Request**: Understand the causes of information loss during support shift handoffs and possible improvements within the selected tracking system and current staffing.
- **Original Input and Clarifications**: Original statement: “I want to understand why tickets get lost during shift handoffs.” Clarifications: support handoffs are the subject; the tracking system is already selected, changing it and increasing staffing are prohibited; existing tools are preferred. Goal and boundaries confirmed.
- **Context, Decisions, and Boundaries**: Context: The user reports that tickets get lost during shift handoffs; this observation has not been independently verified. User decision: The user has already selected the tracking system; reconsidering that choice was not requested. Boundaries: Investigate handoff causes and possible improvements; system replacement and staffing expansion are excluded.
- **Mandatory Constraints and Preferences**: Mandatory constraint: Do not change the selected tracking system or increase staffing. Preference: Prefer existing tools; additional tools are not prohibited if they meet the constraints.
- **Unconfirmed Assumptions and Proposals**: Unconfirmed hypothesis: User hypothesis: information is lost because of verbal handoffs. This is not an established cause. Unconfirmed proposal: The agent proposal to evaluate a handoff checklist is unconfirmed and is not a selected solution.
- **Brief-Preparation Questions**: How are shift roles and hours distributed? Deferred to the brief: the goal, process, and mandatory boundaries are already clear.
- **Future Research Questions**: Which causes of information loss and improvement measures need to be established? Left for research: the causes and suitable measures are not yet known.

##### Example 3 / Option C

- **Confirmed Request**: Understand the causes of information loss during support shift handoffs and possible improvements within the selected tracking system and current staffing.
- **Original Input**: Original statement: “I want to understand why tickets get lost during shift handoffs.”
- **User Clarifications**: The subject is support handoffs; the tracking system is already selected, changing it and increasing staffing are prohibited; existing tools are preferred. Goal and boundaries confirmed.
- **Context**: The user reports that tickets get lost during shift handoffs; this observation has not been independently verified.
- **Decisions**: The user has already selected the tracking system; reconsidering that choice was not requested.
- **Boundaries**: Understand the causes of information loss during support shift handoffs and possible improvements within the selected tracking system and current staffing.
- **Exclusions**: Investigate handoff causes and possible improvements; system replacement and staffing expansion are excluded.
- **Mandatory Constraints**: Do not change the selected tracking system or increase staffing.
- **Preferences**: Prefer existing tools; additional tools are not prohibited if they meet the constraints.
- **Unconfirmed Assumptions and Proposals**: Unconfirmed hypothesis: User hypothesis: information is lost because of verbal handoffs. This is not an established cause. Unconfirmed proposal: The agent proposal to evaluate a handoff checklist is unconfirmed and is not a selected solution.
- **Brief-Preparation Questions**: How are shift roles and hours distributed? Deferred to the brief: the goal, process, and mandatory boundaries are already clear.
- **Future Research Questions**: Which causes of information loss and improvement measures need to be established? Left for research: the causes and suitable measures are not yet known.

##### Example 3 / Option D

- **Confirmed Information**: Request: Understand the causes of information loss during support shift handoffs and possible improvements within the selected tracking system and current staffing. Context: The user reports that tickets get lost during shift handoffs; this observation has not been independently verified. User decision: The user has already selected the tracking system; reconsidering that choice was not requested. Boundaries: Investigate handoff causes and possible improvements; system replacement and staffing expansion are excluded. Mandatory constraint: Do not change the selected tracking system or increase staffing. Preference: Prefer existing tools; additional tools are not prohibited if they meet the constraints.
- **Unconfirmed Statements**: Unconfirmed hypothesis: User hypothesis: information is lost because of verbal handoffs. This is not an established cause. Unconfirmed proposal: The agent proposal to evaluate a handoff checklist is unconfirmed and is not a selected solution.
- **Deferred Questions**: Brief preparation: How are shift roles and hours distributed? Deferred to the brief: the goal, process, and mandatory boundaries are already clear. Future research: Which causes of information loss and improvement measures need to be established? Left for research: the causes and suitable measures are not yet known.
- **Sources and Clarifications**: Original statement: “I want to understand why tickets get lost during shift handoffs.” Clarifications: support handoffs are the subject; the tracking system is already selected, changing it and increasing staffing are prohibited; existing tools are preferred. Goal and boundaries confirmed.

##### Example 3 / Option E

- **Intent**: Understand the causes of information loss during support shift handoffs and possible improvements within the selected tracking system and current staffing.
- **Problem or Need**: The user reports that tickets get lost during shift handoffs; this observation has not been independently verified.
- **Expected Understanding or Decision**: Understand the causes of information loss during support shift handoffs and possible improvements within the selected tracking system and current staffing.
- **Context**: The user reports that tickets get lost during shift handoffs; this observation has not been independently verified.
- **Boundaries**: User decision: The user has already selected the tracking system; reconsidering that choice was not requested. Boundaries: Investigate handoff causes and possible improvements; system replacement and staffing expansion are excluded.
- **Constraints and Preferences**: Mandatory constraint: Do not change the selected tracking system or increase staffing. Preference: Prefer existing tools; additional tools are not prohibited if they meet the constraints.
- **Ambiguities**: No user information justifies a separate section; do not add an internal assessment.
- **Contradictions**: No user information justifies a separate section; do not add an internal assessment.
- **Assumptions**: Unconfirmed hypothesis: User hypothesis: information is lost because of verbal handoffs. This is not an established cause. Unconfirmed proposal: The agent proposal to evaluate a handoff checklist is unconfirmed and is not a selected solution.
- **Research Suitability**: This is the executor's internal assessment, not user content.
- **Addition: Original Input and Clarifications**: Original statement: “I want to understand why tickets get lost during shift handoffs.” Clarifications: support handoffs are the subject; the tracking system is already selected, changing it and increasing staffing are prohibited; existing tools are preferred. Goal and boundaries confirmed.
- **Addition: Deferred Questions**: Brief preparation: How are shift roles and hours distributed? Deferred to the brief: the goal, process, and mandatory boundaries are already clear. Future research: Which causes of information loss and improvement measures need to be established? Left for research: the causes and suitable measures are not yet known.

**Check of recommended Structure B:** all seven sections are used. Do not reopen system selection, weaken the staffing prohibition into a preference, treat the reported observation as proof of the verbal-handoff hypothesis, or declare the checklist a solution. Brief-framing questions remain separate from the causes and measures under investigation.

### 2.5. Why Additional Mandatory Sections Are Not Recommended

| Candidate | Research Conclusion |
|---|---|
| Problem / motivation | Retain when present and material in the request or context. Not every investigation has a separate problem |
| Expected decision | Include in the request if the user wants a decision. Do not force selection on someone seeking an explanation |
| Terms | Retain material definitions in the request or context; no separate mandatory glossary is initially needed |
| Confirmation | The final input's purpose reflects confirmation; recording it belongs to the existing workflow. No separate section is needed to study user-request composition |
| Status, phase log, run history | Outside the studied document's content and excluded by the task |
| Solution evaluation criteria, research method, work plan | Preserve the meaning of explicitly stated user conditions. Do not develop new criteria or plans here; that belongs to the next stage |
| Summary / conclusion | Duplicates the confirmed request without a separate information-transfer obligation |

Conditional inclusion means material information must be retained when present. “Optional” does not permit discarding it to shorten the document. Do not freely add sections between runs; first check whether the information fits an agreed category.

### 2.6. Distribution Check on Two Requests

This checks content without assembling a full Markdown document or combining it with the Part 1 decision.

**Simple synthetic request:** “I want to understand why seasons change on Mars.” The user confirmed this restatement; no additional constraints or separate deferred questions were stated.

| Information | Location |
|---|---|
| Confirmed desire to understand why seasons change on Mars | Confirmed Request |
| Original user statement or accessible reference | Original Input and Clarifications |
| Missing decisions, conditions, and proposals | Omit the remaining sections |

The user's question already appears in the confirmed request. Mandatory repetition in a research-question section adds nothing. No separate “business problem,” solution selection, or research method is needed.

**Complex synthetic request:** the user confirmed investigating personal-photo backup from a home computer for recovery after disk failure. Cloud services are prohibited; the existing external drive is preferred. Operating-system recovery is excluded. An agent proposal to check the value of another copy elsewhere remains unconfirmed and is not an accepted requirement. Photo volume is deferred to brief preparation; local-approach comparison is left for research.

| Information | Location and Qualification |
|---|---|
| Photo-recovery goal and desire to understand backup organization | Confirmed Request |
| Initial statement and material subsequent clarifications | Original Input and Clarifications |
| Exclusion of operating-system recovery | Context, Decisions, and Boundaries |
| Cloud-service prohibition | Mandatory Constraints and Preferences → Mandatory Constraints |
| Preferred use of the existing drive | Mandatory Constraints and Preferences → Preferences |
| Proposal for another copy | Unconfirmed Assumptions and Proposals; do not treat as a selected solution or mandatory research question |
| Photo volume | Brief-Preparation Questions; deferral is acceptable because subject, recovery goal, and exclusions are understood |
| Local-approach comparison | Future Research Questions; deferral is acceptable because the user left approach selection to research |

The complex example uses all seven sections. This demonstrates category coverage, not a requirement to obtain that completeness every time. If the user has not decided whether they want photo or system recovery, that is a blocking ambiguity, not a reason to add an open question to a ready document.

## Using the Findings After a Decision

After the user makes a final decision, the selected representation and section rules will move into a separate template file within `exploration-input-clarification`. At this stage, no template was assembled, no location was selected, and the skill was unchanged.

## Verification, Consistency, and Limitations

Reviewed the updated task, current skill Sections 2–5, and descriptions of workflow purpose in the root README, plugins README, and package README. Recommendations preserve clarified-input boundaries: original input, material clarifications, and content-type distinctions are not replaced by a research brief.

Static checks covered relative links, code fences, option counts in both parts, and changed-file formatting. Verified preservation of one information set across four Part 1 options and coverage of all 15 combinations of three examples and five Part 2 groupings. Qualifications, category distinctions, and required sections were reviewed manually. Sections 2.5 and 2.6 were preserved; end-to-end checks of all options were added in 2.4, while the earlier two-request check in 2.6 remains supplemental. These checks do not establish any agent's extraction accuracy; no skill runs or model trials were performed.

Compared the relevant [documentation](../../../repository-governance/conventions/documentation.md), [repository layout](../../../repository-governance/conventions/repository-layout.md), [skill authoring](../../../repository-governance/conventions/skill-authoring.md), and [change management](../../../repository-governance/conventions/change-management.md) conventions. This research changes neither current policy nor architecture decisions.

Language history: [AGENTS.md](../../../AGENTS.md) and Documentation require American English. The task and report were originally written in Russian at the user's explicit request and subsequently translated into American English at their direction. Repository policy was not changed; the former language exception no longer applies to these translated files. No other discrepancies were found between reviewed descriptions of the current workflow and this research. Proposed conventions remain explicitly separate from existing requirements.
