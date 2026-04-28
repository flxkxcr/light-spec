---
description: Execute tasks, update task status, record testing results and logs
---

Now, your phase is `lsdd-execute`, your phase is `lsdd-execute`

## Input
Spec file: $1
User intent: $2


## Core Objectives

1. Read the provided spec file: $1
2. Execute tasks from the **# Tasks** section
3. Validate results using **# Testing Standards**
4. Update:
  - Task status ([ ] → [x])
  - **## Test Cases** section
  - **# Log** section


## Workflow

### Step 0 — Load Context and Dependencies
- Read `.light-spec-rules/common.md`, you MUST follow all rules defined in this file `.light-spec-rules/common.md`
- Rules in `.light-spec-rules/common.md` take precedence over this command

- If you already read the context and dependeicies just now
  - DO NOT execute `Step 0` again.
- Else:
  - Define the current spec file `$1` as the `entry spec`
  - Execute `Step 0 - Load Context and Dependencies` in `.light-spec-rules/common.md`

### Step 1 — Read Tasks, Requirement, Design and Testing Standards
- Identify all incomplete tasks ([ ])
- Read **# Requirement** section
- Read **# Design** section
- Read **# Testing Standards** section

### Step 2 — Execute Tasks/Test Cases and Update Status

- MUST follow the sequence: Tasks → Test → Mark as completed if tests passed
- MUST execute Phase by Phase (Phase 1 → Phase 2 → ...)

- For each Phase:
  - Execute all tasks
  - Immediately execute the corresponding Test Cases

  - ONLY if all Test Cases pass:
    - MUST check all task checkboxes in this Phase (change [ ] to [x]) (Update ONLY the content inside the `AI task block` under **# Tasks** section in spec file $1)
    - MUST check all corresponding Test Case checkboxes in this Phase (change [ ] to [x]) (Update ONLY the content inside the `AI test block` under **## Test Cases** section in spec file $1)
    - Proceed to the next Phase

  - If any Test Case fails:
    - MUST stop execution immediately
    - MUST report the failure and ask user and wait for user action

Rules:
- ONLY change [ ] → [x] in section **## Test Cases** and section **# Tasks**
- DO NOT modify other content in spec file $1


### Step 3 — Write Log
- Write execution summary to **# Log** section in spec file $1
- Update ONLY the content inside the `AI block` under **# Log** section in spec file $1

- Format: Follow the template file `.light-spec-rules/spec-template.md`

Rules:
- MUST list ALL executed Test Cases
- MUST explicitly mark the result of ALL test cases
- If any Test Case fails, MUST provide a clear and specific failure reason, including concrete evidence (e.g., error message, assertion details, stack trace, or observed incorrect behavior)


## STRICT EDITING RULES
1. DO NOT modify:
  - YAML frontmatter
  - Other sections (Requirement, Design)
  - Any content outside the AI task block

2. If the AI task block or AI test block is missing:
  - DO NOT recreate it
  - Ask the user whether to take control or skip

3. DO NOT rewrite the entire document

4. If there is any content in **# Log** section, you MUST re-write it. DO NOT append.
MUST modify ONLY inside the AI block undef **# Log** section
