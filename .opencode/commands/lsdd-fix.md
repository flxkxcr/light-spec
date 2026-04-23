---
description: Fix the bug with the context in spec file.
agent: plan
---

You are an AI agent executing tasks under the LSDD (Lightweight Spec-Driven Development) protocol.

Now, your phase is `lsdd-fix`, your phase is `lsdd-fix`


## Input

Spec file: $1
Bug description: $ARGUMENTS


## Core Objectives

1. Read the provided spec file: $1
2. Understand the bug description
3. Locate the root cause based on:
   - # Requirement
   - # Design
   - # Tasks
   - # Testing Standards
4. Fix the issue WITHOUT violating the spec
5. Validate the fix using **# Testing Standards**
6. Update:
   - Task status (if affected)
   - **## Test Cases**
   - **# Log**


## Workflow

### Step 0 — Load Context and Dependencies

- Define the current spec file `$1` as the `entry spec`
- Read `.light-spec-rules/common.md`, you MUST follow all rules defined in this file `.light-spec-rules/common.md`
- Rules in `.light-spec-rules/common.md` take precedence over this command
- Execute `Step 0 - Load Context and Dependencies` in `.light-spec-rules/common.md`


### Step 1 — Analyze Bug Context

- Read:
  - **# Requirement**
  - **# Design**
  - **# Tasks**
  - **# Testing Standards**

- Understand the bug from `Bug description`

- Determine:
  - Which requirement is violated
  - Which design assumption is broken
  - Which task(s) are affected
  - Whether existing tests cover the bug

- If the bug cannot be mapped to any requirement or design:
  - STOP
  - Ask user whether:
    1. Update spec
    2. Other (user specify)


### Step 2 — Identify Root Cause

- Analyze the failure source:
  - Implementation error
  - Missing edge case
  - Incorrect design
  - Incomplete requirement
  - Invalid test case

- If existing test cases do NOT cover the bug:
  - You MUST STOP all ongoing work immediately
  - You MUST propose a new test case plan to the user, and ask user

- You MUST:
  - Identify a single clear root cause
  - Avoid speculative or multiple conflicting causes

- If root cause is unclear:
  - STOP and ask user for clarification


### Step 3 — Apply Fix

- Fix the issue based on root cause:

Rules:
- MUST NOT violate:
  - Requirement
  - Design
  - Constitution rules

- MUST NOT:
  - Introduce unrelated changes
  - Refactor beyond necessary scope
  - Add new features

- If fix requires spec change:
  - STOP and ask user before proceeding


### Step 4 — Validate Fix

- Validate using **# Testing Standards**

Rules:
- Tests MUST reflect real behavior
- MUST directly test the affected functionality
- MUST NOT invent results
- You MUST NOT modify the AI test block without user approval

- If validation fails:
  - STOP execution
  - Record failure


### Step 5 — Update Task Status

Update ONLY the content inside the AI task block under **# Tasks** section in spec file $1

- Mark related tasks as:
  - [x] if fix is validated
  - Leave unchanged otherwise

Rules:
- ONLY change [ ] → [x]
- DO NOT modify task descriptions
- DO NOT reorder tasks
- DO NOT delete tasks


### Step 6 — Record Testing Results

Update ONLY the content inside the AI test block under:

**# Testing Standards / ## Test Cases**

- Mark test cases as [x] ONLY if passed

Rules:
- Must correspond to actual validation
- Do NOT invent results


### Step 7 — Write Log

Append to **# Log** section:

```markdown
## YYYY-MM-DD HH:mm

- Action: bug fix
- Bug: <bug short description>
- Root Cause: <identified cause>
- Fix: <summary of fix>
- Result: success / failed
  - Test1: PASS
  - Test2: FAIL (reason: ...)
- Notes: <notes>
```
