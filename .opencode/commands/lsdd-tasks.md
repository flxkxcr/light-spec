---
description: Generate and refine the "Tasks" section of an LSDD spec file
---

You are an AI agent working under the LSDD (Lightweight Spec-Driven Development) protocol.

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
- If you already read the context and dependeicies just now
  - DO NOT execute `Step 0` again.
- Else:
  - Define the current spec file `$1` as the `entry spec`
  - Read `.light-spec-rules/common.md`, you MUST follow all rules defined in this file `.light-spec-rules/common.md`
  - Rules in `.light-spec-rules/common.md` take precedence over this command
  - Execute `Step 0 - Load Context and Dependencies` in `.light-spec-rules/common.md`

### Step 1 — Understand Requirement
- Identify core features
- Identify constraints

### Step 2 — Understand Design
- Identify functions/modules
- Identify processing steps

### Step 3 — Understand Testing Standards
- Identify test actions
- Identify test cases

### Step 4 — Generate Tasks

Update ONLY the content inside the AI block under **# Tasks** section in spec file $1

Tasks MUST:

- Include functionality
- Include test cases
- Show what files will be modified or create
- Be atomic (one clear responsibility)
- Be executable (can be implemented directly)
- Be verifiable (linked to testing)
- Follow logical order


### Task Rules

- Use sequential IDs: T1, T2, T3...
- DO NOT rename or reuse existing task IDs
- DO NOT reorder existing tasks
- DO NOT delete valid existing tasks
- ONLY append new tasks or minimally refine existing ones

### Mapping Rules

- Each key function/module in Design should map to at least one task
- Tasks must collectively satisfy all Testing Standards


## STRICT EDITING RULES

1. ONLY modify content inside the AI task block under **# Tasks**:

   <!-- AI START: TASK -->
   ...
   <!-- AI END: TASK -->

2. DO NOT modify:
   - YAML frontmatter
   - Other sections (Requirement, Design, Testing Standards, etc.)
   - Any content outside the AI task block

3. If the AI task block is missing:
   - DO NOT recreate it
   - Ask the user whether to take control or skip

4. DO NOT rewrite the entire document

5. Modifications must be incremental:
   - DO NOT delete existing valid tasks
   - DO NOT reorder existing tasks
   - ONLY append or minimally refine

6. Each task must remain stable once created:
   - DO NOT change task meaning
   - DO NOT rename task IDs


## TASK RULES

1. ID Rules:
   - Use sequential IDs: T1, T2, T3...

2. Description Rules:
   - Use concise, action-oriented language
   - Avoid vague descriptions
   - MUST explicitly specify the file paths for all create/modify actions and identify the key APIs to be created, modified, or deleted.

3. Dependency Rules:
   - Earlier tasks should enable later tasks
   - Maintain logical execution order

4. Scope Rules:
   - Prefer smaller tasks over large ones
   - Avoid combining unrelated responsibilities

5. Testing Rules:
   - When defining testing tasks:
     - MUST directly invoke the public interface of the module under test
     - DO NOT introduce any intermediate abstractions (e.g., wrappers, helpers, adapters) solely for testing purposes


## TASK FORMAT

Use the following exact format:

- [ ] T<number>: <task description>

Example:

## Phase 1: Core Functionality
- [ ] T1: Update file1.hpp, implement `void function1(string a, int b)`
- [ ] T2: Update file2.ts, implement xxx
- [ ] T3: Create file3.cpp and file3.hpp, implement xxx

## Phase 2: Test
- [ ] T4: Create tests/test1.cpp, test the function `xxx(xxx)`
- [ ] T5: Update tests/test2.cpp tests/test2.hpp, test the xxx pipeline, ...

## Phase 3: Other phase
- [ ] T6: ...


You MUST output the FULL updated markdown document.


## STYLE RULES

- Be concise and structured
- Prefer clarity over abstraction
- Avoid redundancy
- Keep tasks implementation-ready


## FAILURE CONDITIONS

If you:
- Modify content outside Tasks AI task block
- Rewrite entire task list
- Change existing task IDs
- Generate non-executable tasks
- Ignore Requirement / Design / Testing

→ The result is INVALID

Proceed with generating and refining the tasks.