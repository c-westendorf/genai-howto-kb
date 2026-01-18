---
title: GSD+RALPH Method
updated: 2026-01-18
source_attribution: "RALPH method by Geoffrey Huntley, July 2025"
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Writing](writing.md) · [Analysis](analysis.md) · [Research](research.md) · [Code](code.md) · [Meetings](meetings.md) · [DS Patterns](ds_patterns.md) · [MLE Patterns](mle_patterns.md) · [GSD+RALPH](mle_gsd_ralph.md) · [Business](business_patterns.md)

# GSD+RALPH Method

A combined methodology for AI-assisted development:

- **GSD** structures work as a genAI-friendly *spec* (requirements + verifiable success criteria).
- **RALPH** executes the spec via **fresh-context iterations**, persisting state on disk.

> Terminology note: “GSD” is used here as shorthand for a spec-first workflow (Explore → Plan → Code → Commit). It is *not* referring to any specific third-party “GSD” package/tooling.

---

## When to use this

- Complex implementations that span multiple sessions
- Tasks where you've noticed model output degrading over time
- Projects where you want progress to persist but failures to be forgotten
- Long-running work with AI coding assistants (Claude Code, Cursor, Windsurf, etc.)

---

## The core insight

**GSD + RALPH are complementary layers:**

| Layer | What it does | Key artifact |
|-------|-------------|--------------|
| **GSD** (Planning) | Produces a precise, expandable spec | `ralph_task.md` — requirements + success criteria |
| **RALPH** (Execution) | Runs context-clean loops, externalizes state | The restart loop + on-disk plan/ops files |

The spec is the interface between the two.

---

# Part 1: GSD — Task Planning

## The workflow

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

Write the genAI-friendly spec (save as `ralph_task.md`):

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

The `...` tells the model: “Expand this into implementation details.”

**Without expansion markers:**
```text
Create a user authentication system.
```

**With expansion markers:**
```text
Create user authentication:
- Registration endpoint ...
- Login endpoint with JWT ...
- Password hashing with bcrypt ...
- Session management ...
```

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

## Project context files

Provide project-level context via a persistent context file that your code agent loads. Common patterns:

- `CONTEXT.md` or `PROJECT.md` (repo root)
- `.claude/CLAUDE.md` (Claude Code)
- `.cursor/rules.mdc` (Cursor)
- Custom paths configured in your agent

Most code agents walk **up parent directories** from the working directory, loading context files they find along the way.

Example:

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

---

# Part 2: RALPH — Execution Loop

## The core concept

**RALPH is the restart loop: an agent that forgets on purpose.**

Traditional approach: keep context, hope it stays clean
→ context accumulates dead ends, output degrades

RALPH approach: reset context each iteration, persist progress in files
→ each iteration starts fresh, progress survives

---

## The loop

Preferred (official CLI name + print mode):

```bash
while :; do claude -p "$(cat PROMPT.md)"; done
```

Notes:
- Some writeups show `claude-code` in the loop; treat that as an alias/older naming. The portable form is `claude`.
- The loop is intentionally brutal: one run, exit, restart.

This loop:
1. Reads deterministic instructions from `PROMPT.md`
2. Runs a fresh instance
3. When it exits (complete or failed), starts over
4. Progress lives in files, not in chat context

---

## The context pollution problem

### What happens without resets

As agents work on long tasks, context fills with:
- error messages from failed attempts
- abandoned approaches
- debug output
- half-explored ideas

Symptoms:
- repeating itself
- “fixing” the same bug differently each time
- undoing previous fixes
- circular reasoning

### RALPH’s solution

Don’t clean the context — throw it away and re-read reality from disk.

```
Context (polluted)     → dies with each iteration
Files (curated)        → persist across iterations
Git/tests (reality)    → provide backpressure
```

---

## State files

### Preferred artifact split

Keep **three** durable artifacts with clear roles:

1. **Spec (source of truth)** — rarely edited
2. **Implementation plan (living checklist)** — disposable/regenerable
3. **Ops/agent rules (how to run, guardrails)** — brief, stable

Recommended layout:

```
project/
├── ralph_task.md      # requirements/spec (source of truth)
├── progress.md        # what's done / what's next (living, disposable)
├── guardrails.md      # rules to follow (brief, stable)
└── PROMPT.md          # deterministic loop instructions
```

If you prefer a dedicated folder, use `.ralph/`:

```
project/
├── .ralph/
│   ├── ralph_task.md
│   ├── progress.md
│   └── guardrails.md
└── PROMPT.md
```

### Spec (anchor)

This is the GSD-style spec: requirements + success criteria.

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

Tracks what's been completed and what's next. Updated after each iteration. Can be regenerated from the spec if needed.

```markdown
# Progress

## Now
- [ ] Implement POST /users

## Done
- [x] Set up project structure (2026-01-17)
- [x] Implement /health endpoint (2026-01-17)

## Notes / discoveries
- ...
```

### guardrails.md

Rules every iteration must follow. Keep it short and operational.

```markdown
# Guardrails

## How to validate
- Run: npm test

## Always
- Follow existing code patterns in /src
- Update progress.md after each piece of work

## Never
- Modify files outside /src
- Push to main branch directly

## When stuck
- Write a concise failure note into progress.md ("Notes / discoveries")
- Exit cleanly so the next iteration starts fresh
```

### PROMPT.md

What the loop feeds to each iteration:

```markdown
Read ralph_task.md for requirements and success criteria.
Read progress.md for what to work on next.
Read guardrails.md for validation commands and rules.

Do the single highest-priority unfinished item from progress.md.
Run validation.
Update progress.md (mark done, add brief notes).
Commit only if tests pass.
Exit.
```

---

## State hygiene (what makes the loop productive)

**The loop is the mechanism. State hygiene is what keeps it effective.**

Principles:

1. **Externalize all progress** — nothing important lives only in chat context
2. **Clean failure** — failures become short notes in the plan, then the run ends
3. **Atomic updates** — update plan/spec only when work is complete or a decision is finalized
4. **Single source of truth** — requirements live in the spec; the plan is a derived checklist
5. **Keep always-loaded context brief** — avoid auto-loading long logs; summarize into the plan

Iteration checklist:

- [ ] Read spec/plan/agents
- [ ] Do one focused unit of work
- [ ] Run validation
- [ ] Update plan (done + brief notes)
- [ ] Commit only if green
- [ ] Exit

---

## Permissions/autonomy note

If you want truly unattended loops, you need a permissions strategy. Typical practice is to run in a sandboxed environment and enable skip-permissions mode as appropriate for that sandbox.

---

# Part 3: Putting It Together

## The full workflow

```
1. EXPLORE
   └─→ Clarify requirements, identify unknowns

2. PLAN (GSD)
   └─→ Write ralph_task.md with success criteria + expansion markers

3. SET UP (RALPH)
   └─→ Create progress.md and guardrails.md
   └─→ Write PROMPT.md

4. EXECUTE (restart loop)
   └─→ while :; do claude -p "$(cat PROMPT.md)"; done
   └─→ Each iteration: read state → do work → validate → update plan → exit

5. VERIFY + SHIP
   └─→ Ensure all success criteria are checked
   └─→ Commit when green
```

---

## Example: From idea to shipped code

**Idea:** “Add user authentication to the API”

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

**Step 2: Create progress.md**

- Order the work to minimize risk and maximize test feedback.

**Step 3: Run the loop**

```bash
while :; do claude -p "$(cat PROMPT.md)"; done
```

**Step 4: Verify and commit**

When all criteria checked, run `npm test`, then commit.

---

## Common pitfalls

| Pitfall | Signs | Fix |
|---------|-------|-----|
| Vague spec | AI asks many questions | Add expansion markers; make success criteria testable |
| No test command | “It works” but untested | Always include an explicit validation command |
| Treating the plan as truth | Plan drifts from requirements | Keep requirements in spec; regenerate plan if needed |
| Progress lives only in chat | Lost on reset | Update progress.md immediately |
| Always-loaded context bloats | Output degrades again | Keep guardrails.md brief; summarize logs into progress.md |
| Continuing after repeated errors | Same error repeats | End run; restart fresh; change plan/spec only with a decision |

---

## Related

- [One-Shot Planning](../concepts/oneshot_planning.md) — specification model for minimal iteration
- [MLE-Specific Patterns](mle_patterns.md) — additional MLE patterns
- [Code Playbook](code.md) — general code patterns
- [GSD Task Spec Template](../reference/templates/gsd_task_spec.md) — fill-in-the-blank spec
