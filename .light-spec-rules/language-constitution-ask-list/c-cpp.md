# C/C++ Language & Technical Constraints Ask List

**Every question MUST include an "Other (specify)" option, allowing the user to define custom values when none of the predefined options are suitable.**

## Mandatory Constraints (MUST be defined)

### Exception Handling

- Should exceptions be enabled or disabled?
  - Option A: Fully enabled (use standard C++ exceptions)
  - Option B: Disabled (no exceptions allowed)
  - Option C: Restricted (limited usage in specific modules)
  - Option D: Use Structured Exception Handling (SEH) (__try __except) (Windows-specific)



### RTTI (Run-Time Type Information)

- Should RTTI be enabled?
  - Option A: Enabled
  - Option B: Disabled
  - Option C: Partially enabled (only in specific modules)



### Build System

- What build system must be used?
  - Option A: CMake
  - Option B: Makefile
  - Option C: XMake
  - Option D: Visual Studio (.sln)
  - Option E: Other (specify)



### Compiler Compatibility

- Which compilers must be supported?
  - Option A: Multiple (user must specify a list of platforms)
  - Option B: MSVC
  - Option C: GCC
  - Option D: Clang
  - Option E: Intel Compiler (ICC / ICX)
  - Option F: Other



### Platform / OS Constraints

- Which platforms must be supported?
  - Option A: Windows
  - Option B: Linux
  - Option C: macOS
  - Option D: Multiple (user must specify a list of platforms)
  - Option E: Other



### Architecture Constraints

- Which architectures must be supported?
  - Option A: x86 / x64
  - Option B: ARM
  - Option C: Multiple (user must specify a list of platforms)



## Conditional Constraints (Ask ONLY if relevant)

### Naming Conventions (System-Level Only)

- Should naming conventions be strictly enforced?
  - Option A: Yes (define rules)
  - Option B: No (leave flexible)

If YES:
- Class naming style:
  - PascalCase / other
- Function naming style:
  - camelCase / snake_case / other
- Macro naming:
  - UPPER_SNAKE_CASE / other
- And any other questions



### Memory Management Policy

- What memory management model should be enforced?
  - Option A: RAII only (no raw new/delete)
  - Option B: Allow raw pointers
  - Option C: Smart pointers only (unique_ptr/shared_ptr)
  - Option D: Other (user must specify)



### Standard Library Usage

- Are there restrictions on STL usage?
  - Option A: Fully allowed
  - Option B: Restricted (specify)
  - Option C: Disallowed in certain modules (specify)



### Third-Party Libraries

- Are third-party libraries allowed?
  - Option A: Allowed
  - Option B: Restricted (approval required)
  - Option C: Disallowed



### Code Style (Structural Only)

- Should code structure style be enforced?
  - Option A: Yes (brace style, formatting rules)
  - Option B: No



### Module / Interface Constraints

- Should module interfaces follow strict rules?
  - Option A: Yes (define interface constraints)
  - Option B: No



## Classification Rules (For AI)

- Mandatory Constraints:
  - MUST be resolved before proceeding
  - Missing answers MUST block execution

- Conditional Constraints:
  - Ask ONLY if:
    - They affect cross-module consistency
    - They may become enforceable rules
    - They may cause conflicts if undefined

- You MUST NOT:
  - Ask all questions blindly
  - Ask questions already answered
  - Ask about local or implementation-level details