# Common Rules

All the file in `.light-spec/` directory are the `spec file`.


## Spec File Template
All the spec file should be written like the standard spec file `.light-spec-rules/spec-template.md`


## AI Blocks
- `AI block` like this:
<!-- AI START -->
...
<!-- AI END -->

- `AI task block` like this:
<!-- AI START: TASK -->
...
<!-- AI END: TASK -->

- `AI test block` like this:
<!-- AI START: TEST -->
...
<!-- AI END: TEST -->


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
- Start from the `entry spec`

1. Read the spec file:
  - MUST read the FULL file (not partial), including all sections
  - Parse its YAML frontmatter
  - Extract the `dependencies` field

2. For each dependency ID:
  - Locate the corresponding file: `.light-spec/<id>.md`
  - MUST read the FULL file `.light-spec/<id>.md` (not partial)
  - Parse `.light-spec/<id>.md`'s YAML frontmatter
  - Extract `.light-spec/<id>.md`'s `dependencies`

3. Repeat the same process recursively until no dependencies remain

- Dependency resolution MUST be executed only once per run
- If dependencies are already resolved in the current context:
  - DO NOT resolve again


### Git Context Analysis
- Following the `### Dependency Resolution` process:
  - Collect the `git_commit` field from:
    - the `entry spec`
    - all resolved dependency specs

- For every `git_commit` field (both `entry spec` and dependencies):
  1. Run `git show --stat <commit>`, to get a quick overview of changed files
  2. For each changed file:
    - If the file is related to the Requirement, Design, Testing Standards, or Tasks defined in the current spec (`entry spec` or dependency spec):
      - Run `git show <commit> -- <file>`, inspect the changes for the given file

- Rules:
  - `git_commit` MUST contain exactly one commit; otherwise, stop and ask the user for clarification.
  - If `git_commit` is empty or missing:
    - Skip git analysis for that spec

- You MUST process:
  - the `entry spec`
  - AND every dependency spec (no skipping)
