---
title: RALPH State Files Template
updated: 2026-01-17
---

# RALPH State Files Template

Templates for the state files used in RALPH execution. These files externalize state so the AI agent can forget context but remember progress.

---

## Directory structure

```
project/
├── .ralph/
│   ├── ralph_task.md      # Source of truth (GSD spec)
│   ├── progress.md        # What's done / what's next
│   ├── guardrails.md      # Rules to follow
│   ├── errors.log         # What failed
│   └── activity.log       # Audit trail
└── PROMPT.md              # What each iteration reads
```

---

## ralph_task.md

The anchor file. This IS the GSD-style task spec — source of truth for the task.

```markdown
---
task: [short-name]
test_command: "[command to verify]"
---

# Task: [Descriptive Title]

## Context
[Why we're doing this. What exists. Background needed.]

## Success criteria
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]
- [ ] All tests pass

## Implementation

### [Component 1]
- [Requirement] ...
- [Requirement] ...

### [Component 2]
- [Requirement] ...

## Constraints
- [What NOT to do]
- [Patterns to follow]
```

**Note:** Use the [GSD Task Spec Template](gsd_task_spec.md) for detailed examples.

---

## progress.md

Tracks what's been completed and what's next. Updated after each iteration.

```markdown
# Progress

## Completed
- [x] [Step 1] - [timestamp]
- [x] [Step 2] - [timestamp]

## Current
- [ ] [What this iteration should work on]

## Next
- [ ] [Step after current]
- [ ] [Step after that]

## Blocked
[List any blockers with reasons]

---

## Notes
[Optional: observations, decisions made, things to remember]
```

### Example progress.md

```markdown
# Progress

## Completed
- [x] Set up project structure - 2026-01-17 10:30
- [x] Create database schema - 2026-01-17 10:45
- [x] Implement /health endpoint - 2026-01-17 11:00

## Current
- [ ] Implement POST /users endpoint

## Next
- [ ] Implement GET /users endpoint
- [ ] Add input validation
- [ ] Write tests

## Blocked
(none)

---

## Notes
- Using existing db connection pattern from /src/db/index.ts
- Decided on bcrypt for password hashing (rounds=10)
```

---

## guardrails.md

Rules every iteration must follow. Prevents unwanted behavior.

```markdown
# Guardrails

## Always
- Run test command before marking anything complete
- Update progress.md after each piece of work
- Follow existing patterns in the codebase
- Write atomic commits (one logical change per commit)

## Never
- Modify files outside the scope defined in ralph_task.md
- Push directly to main/master branch
- Delete files without logging to activity.log
- Skip tests to mark something "done"

## When stuck
- Log the issue to errors.log with timestamp
- Note what was attempted
- Exit cleanly (don't loop on same error)
- Let next iteration try a fresh approach

## Code standards
- [Add project-specific standards here]
- [E.g., "Use TypeScript strict mode"]
- [E.g., "All functions must have JSDoc"]
```

### Example guardrails.md (MLE project)

```markdown
# Guardrails

## Always
- Run `npm test` before marking task complete
- Update progress.md after each file created/modified
- Use TypeScript strict mode
- Add JSDoc to public functions
- Log activity to activity.log

## Never
- Modify package.json dependencies without noting in progress.md
- Use `any` type in TypeScript
- Push to main branch
- Delete test files
- Ignore linter errors

## When stuck
- Log to errors.log: timestamp, what failed, what was tried
- Exit cleanly
- Next iteration will try fresh approach

## Patterns to follow
- Error handling: use existing pattern in /src/utils/errors.ts
- API responses: use existing pattern in /src/routes/health.ts
- Database queries: use existing pattern in /src/db/queries.ts
```

---

## errors.log

Log of what went wrong. For human review and debugging.

```text
[YYYY-MM-DD HH:MM] ERROR: [description]
  Attempted: [what was tried]
  Result: [what happened]
  Hypothesis: [why it might have failed]

[YYYY-MM-DD HH:MM] ERROR: [description]
  ...
```

### Example errors.log

```text
[2026-01-17 11:15] ERROR: Test suite failed
  Attempted: npm test after implementing POST /users
  Result: 2 tests failed - validation tests
  Hypothesis: Email regex may be wrong, checking pattern

[2026-01-17 11:30] ERROR: Database connection timeout
  Attempted: Query users table
  Result: Connection refused
  Hypothesis: Database container not running, need to start it
```

---

## activity.log

Audit trail of what each iteration did. Useful for debugging stuck loops.

```text
[YYYY-MM-DD HH:MM] Started iteration
[YYYY-MM-DD HH:MM] Read: ralph_task.md, progress.md
[YYYY-MM-DD HH:MM] Working on: [task]
[YYYY-MM-DD HH:MM] Created: [file]
[YYYY-MM-DD HH:MM] Modified: [file]
[YYYY-MM-DD HH:MM] Ran: [command]
[YYYY-MM-DD HH:MM] Result: [pass/fail]
[YYYY-MM-DD HH:MM] Updated: progress.md
[YYYY-MM-DD HH:MM] Exited: [reason - complete/blocked/error]
```

### Example activity.log

```text
[2026-01-17 10:30] Started iteration
[2026-01-17 10:30] Read: ralph_task.md, progress.md, guardrails.md
[2026-01-17 10:30] Working on: Set up project structure
[2026-01-17 10:32] Created: /src/index.ts
[2026-01-17 10:33] Created: /src/routes/health.ts
[2026-01-17 10:34] Ran: npm test
[2026-01-17 10:34] Result: pass (1 test)
[2026-01-17 10:35] Updated: progress.md - marked "Set up project structure" complete
[2026-01-17 10:35] Exited: task complete, moving to next

[2026-01-17 10:36] Started iteration
[2026-01-17 10:36] Read: ralph_task.md, progress.md, guardrails.md
[2026-01-17 10:36] Working on: Create database schema
...
```

---

## PROMPT.md

What the bash loop feeds to each Claude Code iteration.

```markdown
# RALPH Iteration

Read the following files to understand current state:
- .ralph/ralph_task.md — the task definition and success criteria
- .ralph/progress.md — what's done and what to work on next
- .ralph/guardrails.md — rules you must follow

Then:
1. Do the next piece of work from progress.md "Current" section
2. Update .ralph/progress.md when done (move to Completed, set new Current)
3. Log your actions to .ralph/activity.log
4. If you encounter an error, log to .ralph/errors.log and exit
5. Exit when complete or blocked

Remember:
- Do ONE focused task per iteration
- Test before marking complete
- Exit cleanly so next iteration starts fresh
```

---

## Quick setup script

Create all files at once:

```bash
mkdir -p .ralph
touch .ralph/ralph_task.md
touch .ralph/progress.md
touch .ralph/guardrails.md
touch .ralph/errors.log
touch .ralph/activity.log
touch PROMPT.md

echo "# RALPH state files created. Edit ralph_task.md to add your task spec."
```

---

## Related

- [GSD+RALPH Method](../../playbooks/mle_gsd_ralph.md) — the full methodology
- [GSD Task Spec Template](gsd_task_spec.md) — detailed task spec examples
- [One-Shot Planning](../../concepts/oneshot_planning.md) — the underlying mental model
