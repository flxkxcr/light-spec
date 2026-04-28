---
description: Refine and update the "Design" section of an LSDD spec file.
---

Now, your phase is `lsdd-design`, your phase is `lsdd-design`

## Input
Spec file: $1
User intent: $2


## Core Objectives

1. Read the provided spec file: $1
2. Focus ONLY on the **# Design** section
3. Based on the **# Requirement** section, refine and improve the design
4. Update ONLY the AI block inside the Design section
5. ONLY update this file $1, DO NOT modify other files


## Workflow

### Step 0 — Load Context and Dependencies
- Read `.light-spec-rules/common.md`, you MUST follow all rules defined in this file `.light-spec-rules/common.md`
- Rules in `.light-spec-rules/common.md` take precedence over this command

- If you already read the context and dependeicies just now
  - DO NOT execute `Step 0` again.
- Else:
  - Define the current spec file `$1` as the `entry spec`
  - Execute `Step 0 - Load Context and Dependencies` in `.light-spec-rules/common.md`

### Step 1 — Understand Requirement
- Read the **# Requirement** section
- Identify core functionality
- Identify constraints and expected inputs/outputs


### Step 2 — Write Design
Update ONLY the content inside the AI block under **# Design** section in spec file $1.

The design should include:
- High-level architecture (if needed)
- Function/module breakdown
- Data flow (input → processing → output)
- Key interfaces or APIs (keep simple)
- Error handling strategy (if relevant)

Design MUST:
- Follow all constraints defined in **# Requirement**
- Do NOT introduce design patterns unless clearly needed
- MUST explicitly specify the file paths for all create/modify actions and identify the key APIs to be created, modified, or deleted.


## STRICT EDITING RULES

1. ONLY modify content inside the AI block under **# Design**

2. DO NOT modify:
   - YAML frontmatter
   - Other sections (Requirement, Tasks, etc.)
   - Any content outside the AI block

3. If the AI block is missing:
   - DO NOT recreate it
   - Ask the user whether to take control or skip

4. DO NOT rewrite the entire document

5. Modifications must be minimal:
   - Do NOT discard existing valid design
   - Only refine, extend, or reorganize if necessary
