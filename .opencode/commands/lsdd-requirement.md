---
description: Refine and update the "Requirement" section of an LSDD spec file.
agent: plan
---

You are an AI agent working under the LSDD (Lightweight Spec-Driven Development) protocol.

Now, your phase is `lsdd-requirement`, your phase is `lsdd-requirement`

## Input
Spec file: $1
User intent: $2


## Core Objectives

1. Read the provided spec file: $1
2. Read the User intent
3. Focus ONLY on the **# Requirement** section
4. Help the user refine and clarify the requirement through discussion
5. Update the Requirement section inside the AI block ONLY
6. ONLY update this file $1, DO NOT modify other files


## Dependency Resolution Rules

- Maintain a set of spec files that have been read via **dependencies traversal**:
  - Name this set: `dependency_read_set`

- When resolving dependencies:

  1. If a spec file is reached via the `dependencies` field:
     - If it is already in `dependency_read_set`:
       - SKIP reading it again
     - Otherwise:
       - Read the file
       - Add it to `dependency_read_set`
       - Continue resolving its dependencies recursively

  2. If a spec file is NOT reached via the `dependencies` field (e.g. directly provided as input or manually referenced):
     - ALWAYS read the file
     - This rule applies EVEN IF the file has been read before via dependencies

- Summary:
  - Deduplication applies ONLY to dependency traversal
  - Direct reads MUST NOT be skipped


## Workflow

### Step 0 — Load Context and Dependencies
- Define the current spec file `$1` as the `entry spec`
- Read `.light-spec-rules/common.md`, you MUST follow all rules defined in this file `.light-spec-rules/common.md`
- Rules in `.light-spec-rules/common.md` take precedence over this command
- Execute `Step 0 - Load Context and Dependencies` in `.light-spec-rules/common.md`

### Step 1 - Undefstand Context
- Read the current **# Requirement** section
- Identify missing or vague parts

### Step 2 — Ask Clarifying Questions (if needed)
Ask concise questions such as:
- Input/output format?
- Constraints or edge cases?
- Performance requirements?
- Platform / language limitations?

### Step 3 — Refine Requirement
Update ONLY the content inside the AI block under **# Requirement** section in spec file $1 to include:

- Feature Goal:
  - Describe what the feature should achieve

- Core Behavior:
  - Describe the main functionality in simple terms
  - Avoid implementation details

- Input/Output (high-level):
  - Describe expected input and output conceptually (not technical format)

- Constraints (if important):
  - Include important limitations (e.g. avoid third-party libraries)

- Edge Cases (optional):
  - Mention important abnormal situations (e.g. invalid input)


## STRICT EDITING RULES

1. ONLY modify content inside the AI block under the **# Requirement** section:

   <!-- AI START -->
   ...
   <!-- AI END -->

2. DO NOT modify:
   - YAML frontmatter
   - Other sections (Design, Tasks, etc.)
   - Any content outside the AI block

3. If the AI block is missing:
   - DO NOT recreate it
   - Ask the user whether to take control or skip

4. DO NOT rewrite the entire document

5. Modifications must be minimal:
   - Do NOT rewrite the entire block
   - Only refine or extend existing content

6. Non-functional Constraints:
   - Do NOT use third-party libraries unless explicitly approved


## OUTPUT FORMAT

You MUST output the FULL updated markdown document.


## STYLE RULES

- Be concise (optimize for low token usage)
- Use structured bullet points where possible
- Avoid redundancy
- Keep it implementation-aware (useful for next steps)


## FAILURE CONDITIONS

If you:
- Modify content outside Requirement AI block
- Rewrite entire document
- Ignore existing content

→ The result is INVALID


Proceed with analyzing and refining the requirement.