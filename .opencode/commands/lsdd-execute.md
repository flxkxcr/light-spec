---
description: Execute tasks, update task status, record testing results and logs
agent: build
---

You are an AI agent executing tasks under the LSDD (Lightweight Spec-Driven Development) protocol.

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
   - **# Testing Standards / ## Test Cases** section
   - **# Log** section


## Workflow

### Step 0 — Load Context and Dependencies
- Define the current spec file `$1` as the `entry spec`
- Read `.light-spec-rules/common.md`, you MUST follow all rules defined in this file `.light-spec-rules/common.md`
- Rules in `.light-spec-rules/common.md` take precedence over this command
- Execute `Step 0 - Load Context and Dependencies` in `.light-spec-rules/common.md`

### Step 1 — Read Tasks, Requirement, Design and Testing Standards
- Identify all incomplete tasks ([ ])
- Read **# Requirement** section
- Read **# Design** section
- Read **# Testing Standards** section

### Step 2 — Execute Tasks
- Execute tasks sequentially (T1 → T2 → ...)
- After each task:
  - Validate against testing standards

- If a task fails:
  - STOP execution
  - Record failure

- If the task is a testing task:
  - MUST directly invoke the public interface of the module under test
  - DO NOT introduce any intermediate abstractions (e.g., wrappers, helpers, adapters) solely for testing purposes

### Step 3 — Update Task Status
Update ONLY the content inside the AI task block under **# Tasks** section in spec file $1

- AI task block like this:
<!-- AI START: TASK -->
...
<!-- AI END: TASK -->

Action:
- Mark task as [x] ONLY if validated

Rules:
- ONLY change [ ] → [x]
- DO NOT modify task description
- DO NOT reorder tasks
- DO NOT delete tasks

### Step 4 — Record Testing Results
Update ONLY the content inside the AI test block under **# Testing Standards / ## Test Cases** section in spec file $1

- AI test block like this:
<!-- AI START: TEST -->
...
<!-- AI END: TEST -->

Action:
- Mark test cases as [x] ONLY if passed

Rules:
- Must correspond to defined test cases
- Must be based on actual validation
- DO NOT invent results

### Step 5 — Write Log
- Append execution summary to **# Log** section in spec file $1

Format:
```markdown
## YYYY-MM-DD HH:mm

- Executed: T1, T2
- Result: success / partial / failed
  - Test1: PASS
  - Test2: FAIL (reason: ...)
- Notes: <notes>
```

Rules:
- ONLY append
- DO NOT modify previous logs

- If ANY task fails:
  - Ask the user to choose one of the following options:

    1. Continue Iteration:
       - Immediately write a log describing the failure
       - Then proceed to the NEXT execution cycle (do `lsdd-execute` phase again)
       - In the next cycle:
         - Continue performing tasks
         - Continue logging all results (including new failures)

       - IMPORTANT:
         - After this next cycle completes:
           - If ANY task fails again:
             - DO NOT automatically continue
             - MUST ask the user again for the next action

    2. Stop Execution:
       - Immediately stop all ongoing and future actions
       - Write a log describing the failure


## GLOBAL EXECUTION RULES

1. Task execution MUST follow order (T1 → T2 → ...)
2. Each task must be validated before marking as complete
3. If a task fails:
   - STOP further execution (unless explicitly instructed)
   - Record failure
4. NEVER assume success without validation
5. NEVER modify the YAML frontmatter in this spec file $1


## TASK STATUS UPDATE RULES (CRITICAL)

You are ONLY allowed to modify checkbox state:
- [ ] → [x]

You can modify checkbox state ONLY inside the AI task block undef **# Tasks** section:
<!-- AI START: TASK -->
...
<!-- AI END: TASK -->

STRICTLY FORBIDDEN:

- Changing task description
- Reordering tasks
- Deleting tasks
- Renaming task IDs

These rules apply EVEN IF the AI block (or AI task block) is removed.


## TESTING RESULT RULES

Modify ONLY inside:

<!-- AI START: TEST -->
...
<!-- AI END: TEST -->

under **# Testing Standards / ## Test Cases**

### Rules:

- Must correspond to Testing Standards
- Must be factual (based on execution)
- Do NOT invent results


## LOG RULES (APPEND-ONLY)

Modify ONLY inside:

<!-- AI START -->
...
<!-- AI END -->

under **# Log**

### Rules:

- ONLY append at the end
- DO NOT modify previous logs


## OUTPUT FORMAT

You MUST output the FULL updated markdown document.


## FAILURE CONDITIONS

If you:
- Modify task descriptions
- Reorder tasks
- Mark tasks without validation
- Overwrite logs
- Output partial document

→ The result is INVALID

Proceed with executing the tasks.