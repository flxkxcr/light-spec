---
description: Refine and update the "Design" section of an LSDD spec file.
---

You are an AI agent working under the LSDD (Lightweight Spec-Driven Development) protocol.

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
- If you already read the context and dependeicies just now
  - DO NOT execute `Step 0` again.
- Else:
  - Define the current spec file `$1` as the `entry spec`
  - Read `.light-spec-rules/common.md`, you MUST follow all rules defined in this file `.light-spec-rules/common.md`
  - Rules in `.light-spec-rules/common.md` take precedence over this command
  - Execute `Step 0 - Load Context and Dependencies` in `.light-spec-rules/common.md`

### Step 1 — Understand Requirement
- Read the **# Requirement** section
- Identify core functionality
- Identify constraints and expected inputs/outputs

### Step 2 — Evaluate Existing Design
- Check if current design is:
  - Complete
  - Consistent with Requirement
  - Technically feasible

### Step 3 — Improve Design
Update ONLY the content inside the AI block under **# Design** section in spec file $1.

Rules:
- DO NOT modify content outside the AI block
- DO NOT rewrite the entire design
- DO NOT remove valid existing content
- ONLY refine, extend, or minimally reorganize

The design should include:
- High-level architecture (if needed)
- Function/module breakdown
- Data flow (input → processing → output)
- Key interfaces or APIs (keep simple)
- Error handling strategy (if relevant)

### Design Constraints

- Must follow all constraints defined in **# Requirement**
- Prefer simple and direct solutions
- Avoid unnecessary abstraction
- Do NOT introduce design patterns unless clearly needed


## STRICT EDITING RULES

1. ONLY modify content inside the AI block under **# Design**:

   <!-- AI START -->
   ...
   <!-- AI END -->

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


## OUTPUT FORMAT

You MUST output the FULL updated markdown document.


## STYLE RULES

- Be concise and structured
- Prefer bullet points over long paragraphs
- Keep design implementation-oriented
- Avoid unnecessary abstraction


## FAILURE CONDITIONS

If you:
- Modify content outside Design AI block
- Rewrite entire document
- Ignore Requirement section
- Remove valid existing design

→ The result is INVALID


Proceed with refining the design.