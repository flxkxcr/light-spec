---
id: spec-template                               # the name equal to file name
title: example title
keywords: [keyword1, keyword2]
summary: example summary
status: in_progress                             # in_progress | done
git_commit: a1b2c3d (start), abcde1f (end)      # or nothing
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
- [ ] Test1: data test example
  - Purpose: to validate xxx
  - Input: input xxx data
  - Expected Output: output xxx data
  - Validation: check the output data is `xxx`

- [ ] Test2: UI test example
  - Purpose: to validate xxx ui is correct
  - Input: launch the app, and xxx
  - Expected Output: the textarea is xxx, the button is xxx
  - Validation: check xxx element
<!-- AI END: TEST -->

# Tasks
<!-- AI START: TASK -->

## Phase 1: Core Functionality
- [ ] T1: Update file1.hpp, implement xxx
- [ ] T2: Update file2.ts, implement xxx
- [ ] T3: Create file3.cpp and file3.hpp, implement xxx

## Phase 2: Test
- [ ] T4: Create tests/test1.cpp, test the function `xxx(xxx)`
- [ ] T5: Update tests/test2.cpp tests/test2.hpp, test the xxx pipeline, ...

## Phase 3: Other phase
- [ ] T6: ...

<!-- AI END: TASK -->

# Log
<!-- AI START -->
## 2026-04-22 09:46

- Executed: T1, T2, ...
- Result: partial
  - Test1: PASS
  - Test2: FAIL (why failed)
- Notes: xxx

## 2026-04-22 09:50

- Executed: re-check T1, T2, ...
- Result: success
  - Test1: PASS
  - Test2: PASS
- Notes: re-install xxx, and re-run all the tests
<!-- AI END -->
