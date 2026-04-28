---
id: spec-template                               # the name equal to file name
description: example summary
status: in_progress                             # in_progress | done
git_commit: a1b2c3d                             # or nothing
dependencies: [feature-1, feature-2]            # or nothing
---

# Requirement
<!-- AI START -->
- **Feature Goal**:
  - ...
  - ...

- **Core Behavior**:
  - ...
  - ...

- **Input/Output**:
  - ...
  - ...

- **Constraints**:
  - ...
  - ...

- **Edge Cases**:
  - ...
  - ...
<!-- AI END -->

# Design
<!-- AI START -->
- **High-Level Architecture**:
  - ...
  - ...

- **Module Breakdown**:
  - `file1.hpp|cpp`: ...
  - `file2.ts`: ...

- **Layout Design** (if you are designing UI):
  - textarea: ...
  - some button: ...
  - some canvas: ...

- **Key Implementation Details**:
  - ...
  - ...

- **Data Flow**:
  - ...
  - ...

- **File Structure**:
  ```
  example-folder/
  ├── file1    # comment1
  ├── file2    # comment2
  └── file3    # comment3
  ```
<!-- AI END -->

# Testing Standards

## Test Actions
<!-- AI START: TEST -->
`cmake -S . -B build -G "Ninja Multi-Config"`

`cmake --build build --config Release`

`ctest --test-dir build -C Release`
<!-- AI END: TEST -->

## Test Cases
<!-- AI START: TEST -->
- [ ] TC1: data test example
  - Purpose: to validate xxx
  - Input: input xxx data
  - Expected Output: output xxx data
  - Validation: check the output data is `xxx`

- [ ] TC2: UI test example
  - Purpose: to validate xxx ui is correct
  - Input: launch the app, and xxx
  - Expected Output: the textarea is xxx, the button is xxx
  - Validation: check xxx element
<!-- AI END: TEST -->

# Tasks
<!-- AI START: TASK -->

## Phase 1: Core Functionality
- [ ] T1: Update file1, implement `void function1(string a, int b)`
  - Test Cases: TC1

- [ ] T2: Create file2, implement `function2(float a)`
  - Test Cases: TC1, TC2

## Phase 2: Functionality 2
- [ ] T3: Create file3, implement `void function3()` base on file1 `void function1(string a, int b)`
  - Test Cases: TC1

- [ ] T4: Update file1, implement `void function4()` base on file1 `void function1(string a, int b)`
  - Test Cases: TC2

## Phase 3: Test
- [ ] T5: Create tests/test1, test `void function1(string a, int b)` in file1

<!-- AI END: TASK -->

# Log
<!-- AI START -->
## 2026-04-22 09:46

- Executed: T1, T2, ...
- Result: pass / partial / fail
  - TC1: pass
  - TC2: fail (why failed)
- Notes: xxx
<!-- AI END -->
