---
title: GSD Task Spec Template
updated: 2026-01-17
---

> **Navigation**: [START HERE](../../START_HERE.md) · [Concepts](../../concepts/index.md) · [Pitfalls](../../pitfalls/index.md) · [Decisions](../../decisions/index.md) · [Playbooks](../../playbooks/index.md) · [Reference](../index.md)
>
> **In this section**: [Context Pack](context_pack.md) · [Options Table](options_table.md) · [Evidence Table](evidence_table.md) · [GSD Task Spec](gsd_task_spec.md) · [RALPH State Files](ralph_state_files.md)

# GSD Task Spec Template

A template for writing genAI-friendly task specifications. Use `...` as expansion markers to tell the AI where to elaborate.

---

## Full template

```text
---
task: [short-name]
test_command: "[command to verify]"
---

# Task: [Descriptive Title]

## Context
[Why we're doing this. What exists already. Background the AI needs.]

## Success criteria
- [ ] [Testable criterion 1]
- [ ] [Testable criterion 2]
- [ ] [Testable criterion 3]
- [ ] All tests pass

## Scope
IN: [what we're building]
OUT: [what we're NOT building]

## Project structure
```
project/
├── src/
│   └── ...
├── tests/
│   └── ...
└── ...
```

## Data model
[Schema or data structures]
Example: SQLite with tables: id, created, text, tags

## Interface definition
[CLI commands or API endpoints — CLI-style communicates intended behavior]

```
myapp add "text" --tags foo,bar    # Add item
myapp list --tag foo               # List by tag
myapp export --format md           # Export
```

## Dependencies
- [dependency 1]
- [dependency 2]

## Setup instructions
1. [Step 1]
2. [Step 2]

## Guiding example (optional)
Use `ai_docs/[reference_file]` as architectural reference.

## Implementation

### [Component 1]
- [Requirement] ...
- [Requirement] ...

### [Component 2]
- [Requirement] ...
- [Requirement] ...

## Constraints
- [What NOT to do]
- [Boundaries to respect]
- [Patterns to follow]

## Validation
Test command: `[command]`
Generate missing tests if coverage incomplete.

## What "done" means
- All success criteria checked
- All tests pass
- [Any other completion criteria]
```

---

## Minimal template

For smaller tasks:

```text
---
task: [name]
test_command: "[verify]"
---

# [Task]

## Success criteria
- [ ] [Criterion]
- [ ] [Criterion]

## Implementation
- [Requirement] ...
- [Requirement] ...
```

---

## Steering keywords

### The expansion marker: `...`

The `...` tells the AI: "You fill in the implementation details here."

**Without expansion markers:**
```text
Add user authentication
```
→ AI guesses at approach, may not match your intent

**With expansion markers:**
```text
Add user authentication:
- Password hashing with bcrypt ...
- JWT token generation ...
- Token validation middleware ...
```
→ AI knows exactly what to implement, expands each point

### Additional steering keywords

Beyond `...`, use these information-dense keywords:

| Keyword | Meaning | Example |
|---------|---------|---------|
| `...` | "Expand/implement this" | `- Validate input ...` |
| `(mirror X)` | "Repeat the pattern from X" | `// handle error (mirror getUserById)` |
| `(similar to X)` | "Follow existing implementation X" | `- Create endpoint (similar to /health)` |
| `(same pattern)` | "Continue the established pattern" | `- Add remaining CRUD ops (same pattern)` |

**Files as prompt surfaces:** Put steering instructions next to the code they govern. Each file the AI reads is a "prompt surface" — use short, explicit directives rather than long prose.

### Where to use `...`

| Good | Why |
|------|-----|
| `- Validate email format ...` | AI implements validation logic |
| `- Handle not found case ...` | AI writes error handling |
| `- Store in database ...` | AI writes DB interaction |

| Bad | Why |
|-----|-----|
| `- Build the feature ...` | Too vague, defeats purpose |
| `- Do everything ...` | No guidance for AI |

---

## Fill-in examples

### MLE: API endpoint

```text
---
task: users-api
test_command: "npm test"
---

# Task: Users REST API

## Context
Adding to existing Express app in /src. Use existing patterns from /src/routes/health.ts.

## Success criteria
- [ ] GET /users returns list of users
- [ ] GET /users/:id returns single user or 404
- [ ] POST /users creates user with validation
- [ ] All tests pass

## Implementation

### GET /users
- Query all users from database ...
- Return as JSON array ...

### GET /users/:id
- Parse id from params ...
- Query single user ...
- Return 404 if not found ...

### POST /users
- Validate request body (email required, name required) ...
- Check email not already in use ...
- Create user in database ...
- Return created user with 201 ...

## Constraints
- Use existing db connection from /src/db
- Follow error handling pattern from health.ts
- No authentication required (added later)
```

### DS: Analysis task

```text
---
task: churn-analysis
test_command: "pytest tests/test_churn.py"
---

# Task: Churn Factor Analysis

## Context
Monthly churn data in /data/churn.csv. Need to identify top factors for Q2 planning.

## Success criteria
- [ ] Load and validate churn dataset
- [ ] Identify top 3 churn factors with statistical significance
- [ ] Generate visualization of factors
- [ ] Output summary report
- [ ] All tests pass

## Implementation

### Data loading
- Load CSV with pandas ...
- Validate expected columns exist ...
- Handle missing values ...

### Analysis
- Calculate churn correlation with each factor ...
- Apply statistical significance test ...
- Rank factors by impact ...

### Output
- Create bar chart of top factors ...
- Write markdown summary with findings ...

## Constraints
- Use existing viz style from /src/viz/style.py
- Report must be non-technical (for exec audience)
- Include confidence intervals
```

### MLE: Refactoring task

```text
---
task: auth-refactor
test_command: "npm test && npm run lint"
---

# Task: Refactor Auth to Middleware Pattern

## Context
Current auth logic scattered in route handlers. Consolidate into middleware.

## Success criteria
- [ ] Auth logic extracted to /src/middleware/auth.ts
- [ ] All protected routes use middleware
- [ ] No duplicate auth code in handlers
- [ ] Tests still pass
- [ ] Lint passes

## Implementation

### Create middleware
- Extract token parsing from existing handlers ...
- Extract user lookup from existing handlers ...
- Create authRequired middleware function ...

### Update routes
- Replace inline auth in /src/routes/users.ts ...
- Replace inline auth in /src/routes/orders.ts ...
- Add middleware to route definitions ...

### Cleanup
- Remove dead code from handlers ...
- Update any imports ...

## Constraints
- Don't change auth behavior, only structure
- Keep backward compatibility with existing tokens
- One commit per step for easy revert
```

---

## Checklist before using

- [ ] Task has a descriptive title
- [ ] Test command is specified and runnable
- [ ] Success criteria are checkboxes (testable)
- [ ] Implementation has expansion markers (`...`)
- [ ] Constraints explicitly state what NOT to do
- [ ] Context explains what already exists

---

## Common mistakes

| Mistake | Problem | Fix |
|---------|---------|-----|
| No test command | Can't verify completion | Always include `test_command:` |
| Vague criteria | AI doesn't know when done | Make criteria testable checkboxes |
| Missing `...` | AI has to guess approach | Add expansion markers to each requirement |
| Too many criteria | Task too large | Break into smaller specs |
| No constraints | AI makes unwanted changes | State boundaries explicitly |

---

## Expect 90-99% completion, then patch

With a complete spec, the agent generates most of the project in one pass. But expect:
- First pass: 90-99% complete
- Missing: edge cases, test coverage gaps, wiring issues

**The patching workflow:**
1. Run validation command
2. Note failures or gaps
3. Paste error/gap back to agent with minimal commentary
4. Re-run
5. Repeat until green

This is normal — plan for refinement, not perfection on first pass.

---

## Related

- [One-Shot Planning](../../concepts/oneshot_planning.md) — the concept that produces these specs
- [GSD+RALPH Method](../../playbooks/mle_gsd_ralph.md) — how to execute these specs in a loop
- [RALPH State Files](ralph_state_files.md) — state file templates for RALPH execution
- [Context Pack Template](context_pack.md) — general context template
