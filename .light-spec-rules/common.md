# LSDD Common Rules

All the file in `.light-spec/` directory are the `spec file`.


## Spec File Template
All the spec file should be written like the standard spec file `.light-spec-rules/spec-template.md`


## Dependency Resolution Rules

- Maintain a set of spec files that have been read via **dependencies traversal**:
  - Name this set: `dependency_read_set`


### Definition

- A spec file is considered **dependency-derived** ONLY IF:
  - It is discovered from the `dependencies` field in the YAML frontmatter of another spec file

- ONLY dependency-derived files are allowed to be added to `dependency_read_set`


### Resolution Rules

1. When processing the `dependencies` field in YAML frontmatter:

   - For each dependency ID:
     - Locate the corresponding spec file `.light-spec/<id>.md`

     - If the file is already in `dependency_read_set`:
       - SKIP reading it again

     - Otherwise:
       - Read the file
       - Add it to `dependency_read_set`
       - Recursively resolve its dependencies


2. When a spec file is accessed NOT via dependencies (e.g. root input or manual reference):

   - ALWAYS read the file
   - DO NOT add it to `dependency_read_set`
   - This applies EVEN IF the file has already been read via dependencies


### Summary

- `dependency_read_set` ONLY tracks files reached through YAML `dependencies`
- Direct or manual reads are NEVER added to the set
- Deduplication applies ONLY to dependency traversal
- Direct reads MUST NOT be skipped
- Avoid duplicate reads (each dependency file should be read at most once)
- Prevent infinite loops (handle circular dependencies safely)


## Execution Rules

- Dependency resolution MUST be executed only once per run
- If dependencies are already resolved in the current context:
  - DO NOT resolve again


## Priority Rules

- Rules defined in this file MUST be followed by all commands
- These rules take precedence over command-specific instructions


## Step 0 - Load Context and Dependencies

### Constitution Enforcement
- If `.light-spec-rules/constitution.md` does NOT exist:
  - You MUST stop all execution immediately
  - You MUST NOT proceed with any further steps
  - You MUST ask the user to create this file before continuing

- You MUST read `.light-spec-rules/constitution.md`
- You MUST follow all rules defined in this file

- If any conflict occurs between:
  - the constitution
  - other rules
  - or task instructions

  - You MUST:
    - Detect and explicitly describe the conflict
    - Present the conflicting options clearly
    - Ask the user to decide which rule or instruction to follow

  - You MUST NOT:
    - Automatically resolve the conflict
    - Ignore the conflict


### Dependency Resolution
- Follow the **Dependency Resolution Rules**
  - Read the YAML frontmatter in file `entry spec`
  - Extract the `dependencies` field in file `entry spec`
  - Resolve all dependencies recursively in file `entry spec`
  - Ensure dependency resolution is executed only once


### Git Context Analysis

#### 1. Entry Spec
- Extract the `git_commit` field from the YAML frontmatter of the `entry spec` file.

#### 2. Dependency Specs (IMPORTANT)
- Iterate over **ALL dependency spec files**.
- For each dependency spec file:
  - Read its YAML frontmatter
  - Extract the `git_commit` field

#### 3. Git Commit Interpretation
For every `git_commit` field (both entry spec and dependencies):

- If `git_commit` contains ONE commit:
  - Run:
    - `git show <commit>`
  - Use this to inspect the changes introduced by the feature

- If `git_commit` contains TWO commits:
  - Treat them as: `[start, end]`
  - Run:
    - `git diff <start> <end>`
  - Prefer this over inspecting individual commits

- Optionally:
  - Run `git diff --name-only <start> <end>` to identify affected files

- If `git_commit` is empty or missing:
  - Skip git analysis for that spec

#### 4. Execution Requirement
- You MUST process:
  - the `entry spec`
  - AND every dependency spec (no skipping)
