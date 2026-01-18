---
title: GSD+RALPH Method
updated: 2026-01-17
source_attribution: "RALPH method by Geoffrey Huntley, July 2025"
---

# GSD+RALPH Method

A combined methodology for AI-assisted development: **GSD** structures tasks as genAI-friendly specs, **RALPH** executes them without context pollution.

---

## When to use this

- Complex implementations that span multiple sessions
- Tasks where you've noticed AI output degrading over time
- Projects where you want progress to persist but failures to be forgotten
- Long-running work with Claude Code or similar AI coding assistants

---

## The core insight

**GSD + RALPH are complementary layers:**

| Layer | What it does | Key artifact |
|-------|-------------|--------------|
| **GSD** (Planning) | Structures tasks as genAI-friendly specs | `ralph_task.md` — the task spec |
| **RALPH** (Execution) | Runs context-clean loops, externalizes state | The bash loop + state files |

The `ralph_task.md` file IS the GSD-style spec — this is where the two methods connect.

---

# Part 1: GSD — Task Planning

## The GSD workflow

```
┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐
│ EXPLORE │ → │  PLAN   │ → │  CODE   │ → │ COMMIT  │
│         │    │         │    │         │    │         │
│ Clarify │    │  Write  │    │Implement│    │ Verify  │
│ Scope   │    │  Spec   │    │  Code   │    │  Ship   │
└─────────┘    └─────────┘    └─────────┘    └─────────┘
```

### Explore phase

Understand before acting:

```text
I need to: [task description]

Before we start:
1. What clarifying questions do you have?
2. What are the key technical decisions?
3. What existing code/patterns should we follow?
4. What are the risks or edge cases?
```

### Plan phase

Write the genAI-friendly spec (this becomes `ralph_task.md`):

```text
Based on our exploration, write a task spec with:

1. Clear task definition
2. Success criteria as checkboxes
3. Test command to verify
4. Expansion points marked with "..."
5. Constraints and guardrails
```

### Code phase

Implement according to spec:

```text
Implement the next unchecked item from the success criteria.

After implementation:
- Show what was created/changed
- Update progress
- Note what to verify
```

### Commit phase

Verify and ship:

```text
Before committing:
1. Run test command
2. Check all success criteria
3. Review for missed edge cases
4. Write commit message
```

---

## Writing genAI-friendly task specs

### The "..." expansion marker

This is the key to genAI-friendly specs. The `...` tells the AI: "You expand this."

**Without expansion markers:**
```text
Create a user authentication system.
```
→ AI makes many assumptions, output may not match intent

**With expansion markers:**
```text
Create user authentication:
- Registration endpoint ...
- Login endpoint with JWT ...
- Password hashing with bcrypt ...
- Session management ...
```
→ AI knows exactly what to implement, expands each point

### Task spec structure

```text
---
task: [short name]
test_command: "[how to verify]"
---

# Task: [descriptive title]

## Context
[Why we're doing this, what exists already]

## Success criteria
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

## Implementation

### [Component 1]
- [Requirement] ...
- [Requirement] ...

### [Component 2]
- [Requirement] ...

## Constraints
- [What NOT to do]
- [Boundaries to respect]
```

---

## Context via CLAUDE.md

Provide project-level context in a `CLAUDE.md` file:

```markdown
# Project: [Name]

## Architecture
[Brief architecture description]

## Conventions
- [Language/framework conventions]
- [Naming conventions]
- [File organization]

## Testing
- [Test framework]
- [Coverage requirements]

## Patterns to follow
- [Pattern 1]
- [Pattern 2]

## Avoid
- [Anti-pattern 1]
- [Anti-pattern 2]
```

Place at:
- Repository root for project-wide context
- Subdirectories for area-specific context

---

# Part 2: RALPH — Execution Loop

## The core concept

**RALPH is an agent that forgets on purpose.**

Traditional approach: Keep context, hope it stays clean
→ Context accumulates errors, output degrades

RALPH approach: Reset context each iteration, persist progress in files
→ Each iteration starts fresh, progress survives

## The bash loop

```bash
while :; do cat PROMPT.md | claude-code ; done
```

This loop:
1. Reads current task from `PROMPT.md`
2. Runs Claude Code with that context
3. When Claude Code exits (complete or failed), starts fresh
4. Progress lives in files, not in context

---

## The context pollution problem

### What happens without RALPH

As AI agents work on long tasks, context fills with:
- Error messages from failed attempts
- Abandoned approaches
- Debugging output
- Half-baked explorations

**Symptoms of context pollution:**
- Repeating itself
- "Fixing" the same bug differently each time
- Undoing its own previous fixes
- Circular reasoning

**The trap:** Adding more instructions doesn't help. More tokens don't help. Once context is polluted, quality only degrades.

### RALPH's solution

Don't clean the context — throw it away and start fresh.

```
Context (polluted)     →  Dies with each iteration
Files (clean)          →  Persist forever
Git (authoritative)    →  Can't hallucinate
```

Each fresh agent reads reality from files, not from polluted memory.

---

## State files

### Directory structure

```
project/
├── .ralph/
│   ├── ralph_task.md      # The GSD spec (source of truth)
│   ├── progress.md        # What's done / what's next
│   ├── guardrails.md      # Rules to follow
│   ├── errors.log         # What blew up
│   └── activity.log       # Audit trail
└── PROMPT.md              # What each iteration reads
```

### ralph_task.md (Anchor file)

This IS the GSD-style spec. Source of truth for the task:

```markdown
---
task: build a REST API
test_command: "npm test"
---

# Task: REST API

## Success criteria
- [ ] GET /health returns 200
- [ ] POST /users creates a user
- [ ] All tests pass

## Implementation
...
```

### progress.md

Track completed work:

```markdown
# Progress

## Completed
- [x] Set up project structure - 2026-01-17 10:30
- [x] Implement /health endpoint - 2026-01-17 10:45

## Current
- [ ] Implement POST /users

## Blocked
(none)
```

### guardrails.md

Rules every iteration must follow:

```markdown
# Guardrails

## Always
- Run tests before marking anything complete
- Update progress.md after each change
- Follow existing code patterns in /src

## Never
- Modify files outside /src
- Push to main branch directly
- Delete without backup

## When stuck
- Log to errors.log
- Exit cleanly
- Let next iteration try fresh
```

### PROMPT.md

What the loop feeds to each iteration:

```markdown
Read .ralph/ralph_task.md for the task.
Read .ralph/progress.md for current status.
Read .ralph/guardrails.md for rules.

Do the next piece of work.
Update .ralph/progress.md when done.
Exit when complete or blocked.
```

---

## State hygiene

**The core technique of RALPH is state hygiene, not the loop.**

### Principles

1. **Externalize all progress** — Nothing important lives only in context
2. **Clean failure** — Errors get logged, then forgotten
3. **Atomic updates** — Files reflect completed work, not work-in-progress
4. **Single source of truth** — `ralph_task.md` is authoritative
5. **Human override** — Edit files between iterations as needed

### Hygiene checklist

Each iteration should:
- [ ] Read current state from files
- [ ] Do ONE focused piece of work
- [ ] Update progress.md with completion
- [ ] Log any errors to errors.log
- [ ] Update ralph_task.md if scope changes
- [ ] Exit cleanly

---

# Part 3: Putting It Together

## The full workflow

```
1. EXPLORE
   └─→ Clarify requirements, identify unknowns

2. PLAN (GSD)
   └─→ Write ralph_task.md with success criteria + expansion markers

3. SET UP (RALPH)
   └─→ Create .ralph/ directory with state files
   └─→ Write PROMPT.md
   └─→ Write guardrails.md

4. EXECUTE (RALPH loop)
   └─→ while :; do cat PROMPT.md | claude-code ; done
   └─→ Each iteration: read state → do work → update progress → exit

5. VERIFY
   └─→ Run test_command
   └─→ Check all success criteria
   └─→ Commit when green
```

## Example: From idea to shipped code

**Idea:** "Add user authentication to the API"

**Step 1: Write ralph_task.md (GSD spec)**

```markdown
---
task: user-auth
test_command: "npm test"
---

# Task: User Authentication

## Context
Adding auth to existing Express API in /src/api

## Success criteria
- [ ] POST /auth/register creates user with hashed password
- [ ] POST /auth/login returns JWT on valid credentials
- [ ] Protected routes reject requests without valid JWT
- [ ] All tests pass

## Implementation

### Registration
- Validate email format ...
- Hash password with bcrypt ...
- Store user in database ...
- Return user without password ...

### Login
- Find user by email ...
- Compare password hash ...
- Generate JWT with user ID ...
- Return token ...

### Middleware
- Extract token from Authorization header ...
- Verify JWT ...
- Attach user to request ...

## Constraints
- Use existing User model pattern
- JWT secret from environment
- Don't modify existing endpoints
```

**Step 2: Set up RALPH state files**

Create `.ralph/` with progress.md, guardrails.md, errors.log, activity.log

**Step 3: Run the loop**

```bash
while :; do cat PROMPT.md | claude-code ; done
```

Watch progress.md update as work completes. If iteration fails, next one starts fresh.

**Step 4: Verify and commit**

When all criteria checked, run `npm test`, then commit.

---

## Common pitfalls

| Pitfall | Signs | Fix |
|---------|-------|-----|
| Vague spec | AI asks many questions | Add expansion markers, be specific |
| No test command | "It works" but untested | Always include verification command |
| Progress in context only | Lost on reset | Write to progress.md immediately |
| Continuing after errors | Same error repeats | Exit and restart fresh |
| Stale ralph_task.md | Working on wrong thing | Update task file as scope evolves |
| Missing guardrails | Unwanted changes | Add explicit rules |
| No activity logging | Can't debug stuck loops | Always log to activity.log |

---

## Related

- [One-Shot Planning](../concepts/oneshot_planning.md) — the underlying mental model
- [MLE-Specific Patterns](mle_patterns.md) — additional MLE patterns
- [Code Playbook](code.md) — general code patterns
- [GSD Task Spec Template](../reference/templates/gsd_task_spec.md) — fill-in-the-blank spec
- [RALPH State Files Template](../reference/templates/ralph_state_files.md) — state file templates
- [Context Engineering](../concepts/context_engineering.md) — context packaging fundamentals
