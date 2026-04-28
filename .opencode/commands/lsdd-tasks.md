---
description: Generate and refine the "Tasks" section of an LSDD spec file
---

Now, your phase is `lsdd-tasks`, your phase is `lsdd-tasks`

## Input
Spec file: $1  
User intent: $2


## Core Objectives

1. Read the provided spec file: $1
2. Focus ONLY on the **# Tasks** section
3. Derive implementation tasks from Requirement, Design, and Testing Standards
4. Generate clear, atomic, executable tasks
5. Update ONLY the AI task block inside the **# Tasks** section
6. ONLY update this file $1, DO NOT modify other files


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
Read the **# Requirement** section:

- Identify core features
- Identify constraints


### Step 2 — Understand Design
Read the **# Design** section:

- Identify functions/modules
- Identify processing steps


### Step 3 — Understand Testing Standards
Read the **# Testing Standards** section:

- Identify test actions
- Identify test cases


### Step 4 — Generate Tasks

Update ONLY the content inside the AI block under **# Tasks** section in spec file $1

Follow Requirement, Design, Testing Standards, and generate tasks.

Rules:
- MUST follow the spec file template `.light-spec-rules/spec-template.md`
- MUST follow the Requirement, Design, Testing Standards
- MUST show what files and key APIs will be modified / created / deleted

- MUST use sequential IDs: T1, T2, T3...
- Include functionality
- Include test cases (if it has)
- Be atomic (one clear responsibility)
- Prefer smaller tasks over large ones, avoid combining unrelated responsibilities

- When defining testing tasks:
  - MUST directly invoke the public interface of the module under test
  - DO NOT introduce any intermediate abstractions (e.g., wrappers, helpers, adapters) solely for testing purposes

- MUST use `Phase N - <description>` to structure tasks
  - Tasks within the same Phase MUST have no dependencies and MUST be executable in parallel
  - Tasks that modify the same file MUST NOT be placed in the same Phase
  - Tasks with dependencies MUST be separated into different Phases
  - Each Phase MUST depend only on previous Phases, never on tasks within the same Phase

- Each Task MUST be covered by at least one Test Case
- During task generating:
  - If a Task is NOT covered by any Test Case in the Testing Standard section:
    - MUST immediately stop all work
    - MUST NOT proceed with incomplete test coverage
  - MUST ask the user how to proceed with the following options:
    - A: Let the AI agent generate and add the missing Test Case(s)
    - B: Let the user manually provide the Test Case(s)
  - MUST wait for user input before continuing

- All non-testing Tasks MUST mark the corresponding test cases such as: `Test Cases: TC1, ...`, the format MUST follow the template spec file `.light-spec-rules/spec-template.md`
- Testing Tasks (e.g., tasks that create or modify test code) MUST NOT include test cases info
- Missing or malformed test cases info MUST be treated as missing test coverage


## STRICT EDITING RULES

1. ONLY modify content inside the AI task block under **# Tasks**

2. DO NOT modify:
  - YAML frontmatter
  - Other sections (Requirement, Design, Testing Standards, etc.)
  - Any content outside the AI task block

3. If the AI task block is missing:
  - DO NOT recreate it
  - Ask the user whether to take control or skip

4. DO NOT rewrite the entire document
