---
description: Create or update a constitution for the project
agent: plan
---

You are an AI agent responsible for creating or updating the LSDD (Lightweight Spec-Driven Development) constitution file for the project.

All the file in `.light-spec/` directory are the `spec file`.

The constitution is located at:
`.light-spec-rules/constitution.md`

This is NOT the constitution itself.  
This is a command that defines how the constitution must be generated.

The constitution must ONLY contain:
- Conflict resolution rules
- Execution blocking conditions
- Non-negotiable constraints

The constitution MUST NOT contain:
- Architecture design
- Requirement definitions
- Implementation details
- Tool preferences (unless strictly required)


## Input

User intent: $1


## Core Objectives

- Extract enforceable rules from user intent and project context
- Ensure all rules are explicit, atomic, and conflict-resolvable
- Prevent non-constitutional content from entering the constitution
- Maintain minimal and strict rule set


## Workflow

### Step 1 - Analyze Existing Context

- Check if `.light-spec-rules/constitution.md` exists
  - If exists → read and analyze current rules
  - If not → prepare to create a new constitution

- Check if any `spec file` in directory `.light-spec/`
  - Iterate all `spec files`
  - For each spec file:
    - Read and analyze the following sections:
      - Requirement
      - Design
      - Testing Standards
      - Tasks
      - Log

    - Identify potential rule candidates from:
      - Repeated constraints across multiple specs
      - Explicit "must", "must not", "always", "never" statements
      - Testing-related enforcement rules
      - Execution blocking conditions

    - For each candidate:
      - DO NOT immediately convert into constitution rule
      - Mark it as a "rule candidate" for further validation

- Scan project files to identify:
  - Existing enforced constraints
  - Repeated conflict patterns
  - Implicit rules that may require formalization

- DO NOT automatically convert conventions into rules
- Only extract rules that are:
  - Enforceable
  - Conflict-relevant


### Step 2 - Ask User for Clarification

You MUST ask the user if:

- A potential rule is ambiguous
- Multiple conflicting rules are detected
- A rule may restrict future flexibility
- It is unclear whether something should be a rule or a preference

Questions MUST:
- Be specific
- Reference the exact uncertainty
- Avoid assumptions
- Provide multiple concrete options when applicable
- For each option:
  - Clearly describe the choice
  - Analyze trade-offs (pros and cons)
- Highlight risks or long-term impact if relevant
- If a default or recommended option exists, you MAY suggest it, but MUST NOT enforce it


### Step 3 - Resolve Language & Technical Constraints

#### 3.1 Detect Existing Technical Context
- Analyze project files and spec files to determine:
  - Programming language(s)
  - Frameworks or major libraries
  - Existing technical constraints (if explicitly defined)

- If such information is explicitly defined:
  - DO NOT re-ask the same information
  - Only mark uncertainties or inconsistencies for clarification

- If language or tech-stack cannot be determined:
  - You MUST ask the user


#### 3.2 Validate and Complete Context
- If partial or inferred information exists:
  - Ask the user to confirm detected language(s) and stack
  - Ask for missing critical components ONLY

- You MUST NOT:
  - Ask about already defined information
  - Ask about local or non-impactful implementation details


#### 3.3 Language-Specific Clarification (Conditional)
- If a supported language is identified:
  - Load the corresponding ask list

Supported ask lists:
- C/C++: `.light-spec-rules/language-constitution-ask-list/c-cpp.md`
- JavaScript/TypeScript: `.light-spec-rules/language-constitution-ask-list/js-ts.md`

- From the ask list:
  - Classify questions into:
    1. Mandatory Constraints:
       - Fundamental language or system-level constraints
       - MUST be defined for correct implementation

    2. Conditional Constraints:
       - Style, preference, or non-critical constraints
       - Only required if they affect consistency or may cause conflicts

- For Mandatory Constraints:
  - If already clearly defined → DO NOT ask
  - If missing or unclear → You MUST ask the user

- For Conditional Constraints:
  - Ask ONLY IF:
    - They may cause inconsistency across modules
    - They may introduce conflicts if undefined

- You MUST NOT:
  - Ask questions that are already clearly defined
  - Ask irrelevant or purely local implementation questions


#### 3.4 Questioning Rules
All questions MUST follow:

- Be specific
- Avoid assumptions
- Provide multiple concrete options when applicable
- For each option:
  - Clearly describe the choice
  - Analyze trade-offs (pros and cons)
- Highlight risks or long-term impact if relevant
- If a default or recommended option exists, you MAY suggest it, but MUST NOT enforce it


#### 3.5 Execution Constraints
- This step MUST be completed before Step 4
- If critical technical constraints remain undefined:
  - You MUST NOT proceed to Step 4
- You SHOULD minimize unnecessary questioning to avoid interrupting the workflow


### Step 4 - Create or Update Constitution File

- Update or write content to `.light-spec-rules/constitution.md`

- You MUST follow the structure defined in `.light-spec-rules/constitution-template.md`

- The constitution MUST contain ONLY the following sections:
  - Requirement Constraints
  - Design Constraints
  - Testing Standards Constraints
  - Tasks Constraints
  - Log Constraints

- You MUST map all confirmed rules into the correct section:
  - Requirement-related rules → Requirement Constraints
  - Design or architecture constraints → Design Constraints
  - Test-related rules → Testing Standards Constraints
  - Task execution or workflow rules → Tasks Constraints
  - Logging and traceability rules → Log Constraints
  - Language and technical constraints:
    - MUST be classified under Design Constraints by default
    - MUST NOT create a separate section for them
    - Exception handling (reclassification rules):
        - If a constraint directly affects testing behavior → Testing Standards Constraints
        - If a constraint directly affects task execution or workflow → Tasks Constraints
        - If a constraint directly affects logging or traceability → Log Constraints

- You MUST:
  - Classify each rule based on its primary impact
  - Avoid duplicating the same rule across multiple sections

- You MUST NOT:
  - Modify the constitution title **# Project Constitution**
  - Create new sections
  - Merge sections
  - Place rules in incorrect sections

- If a section has no applicable rules:
  - Leave the section empty
  - DO NOT generate placeholder content

- When creating or updating:
  - ONLY include rules confirmed during previous steps
  - REMOVE any non-constitutional content

- Each rule MUST:
  - Be atomic (single responsibility)
  - Be enforceable (can trigger stop or decision)
  - Be unambiguous

- DO NOT include:
  - Any content not explicitly confirmed by the user

- If updating:
  - Preserve existing valid rules
  - Modify only conflicting or outdated rules
  - Reclassify rules if they are in the wrong section


## Rule Inclusion Criteria

A rule can be included ONLY if:

- It resolves a potential conflict
- It defines a blocking condition
- It enforces a non-negotiable constraint

A rule MUST NOT be included if it is:

- A coding style suggestion
- A tool preference
- A design pattern recommendation
- A convenience guideline
