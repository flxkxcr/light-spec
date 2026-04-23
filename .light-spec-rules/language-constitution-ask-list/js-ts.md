# JavaScript / TypeScript Language & Technical Constraints Ask List

**Every question MUST include an "Other (specify)" option, allowing the user to define custom values when none of the predefined options are suitable.**

## Mandatory Constraints (MUST be defined)

### Language Mode

- What language mode should be used?
  - Option A: JavaScript (no TypeScript)
  - Option B: TypeScript (strict mode)
  - Option C: Mixed (JS + TS allowed, specify boundaries)



### TypeScript Strictness (if TypeScript is used)

- What level of strictness must be enforced?
  - Option A: strict: true (full strict mode)
  - Option B: Partial strict mode (specify relaxed rules)
  - Option C: Non-strict TypeScript



### Runtime Environment

- What runtime must be used?
  - Option A: Node.js
  - Option B: Browser
  - Option C: Both (universal)
  - Option D: Other (specify)



### Module System

- What module system must be used?
  - Option A: ES Modules (import/export)
  - Option B: CommonJS (require/module.exports)
  - Option C: Mixed (specify boundaries)
  - Option D: Other (specify)



### Package Manager

- What package manager must be used?
  - Option A: npm
  - Option B: yarn
  - Option C: pnpm
  - Option D: Other (specify)



## Conditional Constraints (Ask ONLY if relevant)


### Linting / Formatting Rules

- Should linting be strictly enforced?
  - Option A: Yes (define rules as mandatory)
  - Option B: No

If YES:
- Which linter must be used?
  - ESLint / Other (specify)

- Which formatter must be used?
  - Prettier / Other (specify)



### State Management Constraints (Frontend)

- Is global state management required?
  - Option A: No global state
  - Option B: Redux
  - Option C: Zustand
  - Option D: Other (specify)



### Framework Constraints

- Is a framework required?
  - Option A: No framework
  - Option B: React
  - Option C: Vue
  - Option D: Next.js
  - Option E: Other (specify)



### Async Model Constraints

- What async handling model must be enforced?
  - Option A: async/await only
  - Option B: Promises only
  - Option C: Mixed (specify rules)



### Error Handling Policy

- What error handling strategy must be used?
  - Option A: try/catch only
  - Option B: Result-style (no exceptions)
  - Option C: Mixed (specify rules)



### Browser Compatibility (if applicable)

- What browser targets must be supported?
  - Option A: Modern browsers only
  - Option B: Last 2 versions
  - Option C: Legacy support (specify)



## Classification Rules (IMPORTANT)

- Mandatory Constraints:
  - MUST be resolved before proceeding
  - Missing answers MUST block constitution generation

- Conditional Constraints:
  - Ask ONLY IF:
    - It affects cross-module consistency
    - It may become enforceable rule
    - It may cause conflict if undefined

- You MUST NOT:
  - Ask all questions blindly
  - Ask irrelevant local implementation details
  - Repeat already defined constraints