---
description: Define and refine the "Testing Standards" section of an LSDD spec file
agent: plan
---

You are an AI agent working under the LSDD (Lightweight Spec-Driven Development) protocol.

Now, your phase is `lsdd-testing-standards`, your phase is `lsdd-testing-standards`

## Input
Spec file: $1  
User intent: $2


## Core Objectives

1. Read the provided spec file: $1
2. Focus ONLY on the **# Testing Standards** section
3. Derive test cases from **# Requirement** and **# Design** section
4. Define clear, verifiable testing standards
5. Update ONLY the AI test block inside the **# Testing Standards** section
6. ONLY update this file $1, DO NOT modify other files


## Workflow

### Step 0 — Load Context and Dependencies
- Define the current spec file `$1` as the `entry spec`
- Read `.light-spec-rules/common.md`, you MUST follow all rules defined in this file `.light-spec-rules/common.md`
- Rules in `.light-spec-rules/common.md` take precedence over this command
- Execute `Step 0 - Load Context and Dependencies` in `.light-spec-rules/common.md`

### Step 1 — Understand Requirement
- Identify expected behavior
- Identify input/output format
- Identify constraints

### Step 2 — Understand Design
- Identify key functions/modules
- Identify data flow
- Identify critical logic paths

### Step 3 — Define Test Cases
Update ONLY the content inside the AI test block under **# Testing Standards** section in spec file $1

- Read **## Test Actions** section.
   - If it is empty:
   - You MUST stop and ask user how to test.
   - You MUST NOT infer, generate, or assume any test actions.

- Define test cases under **## Test Cases** section
Each test case MUST follow this EXACT format:

- [ ] Test<number>: <short description>
  - Purpose:
  - Input:
  - Expected Output:
  - Validation:

### Rules

- Expected Output MUST be concrete and verifiable (no vague terms like "correct result")
- Validation MUST describe how to determine PASS / FAIL
- Test cases MUST be consistent with Requirement
- Use sequential IDs: Test1, Test2, Test3...

### Coverage Requirements

Test cases MUST include:

- Normal cases
- Edge cases (e.g. empty input, invalid format)
- Error handling
- Boundary conditions (if applicable)


## STRICT EDITING RULES

1. ONLY modify content inside the AI test block under **# Testing Standards**:

   <!-- AI START: TEST -->
   ...
   <!-- AI END: TEST -->

2. DO NOT modify:
   - YAML frontmatter
   - Other sections (Requirement, Design, Tasks, etc.)
   - Any content outside the AI test block

3. If the AI test block is missing:
   - DO NOT recreate it
   - Ask the user whether to take control or skip

4. DO NOT rewrite the entire document

5. Modifications must be minimal:
   - Do NOT discard valid existing test cases
   - Only refine, extend, or clarify


## TESTING COVERAGE

Ensure coverage of:

1. Normal cases
2. Edge cases
3. Error handling (invalid input, empty input, etc.)
4. Boundary conditions (if applicable)


## OUTPUT FORMAT

You MUST output the FULL updated markdown document.


## STYLE RULES

- Be precise and testable (avoid vague wording)
- Prefer structured bullet points
- Avoid implementation details
- Keep concise


## FAILURE CONDITIONS

If you:
- Modify content outside Testing Standards AI test block
- Output only partial document
- Write non-verifiable tests (e.g. "should work correctly")
- Ignore Requirement or Design

→ The result is INVALID

Proceed with defining the testing standards.