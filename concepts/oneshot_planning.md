---
title: One-Shot Planning
updated: 2026-01-18
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Context Engineering](context_engineering.md) · [Explore → Select → Refine](explore_select_refine.md) · [Trust Calibration](trust_calibration.md) · [Parallel Execution](parallel_execution.md) · [Decision Flow](decision_flow.md) · [One-Shot Planning](oneshot_planning.md)

# One-Shot Planning

## What it is

One-shot planning is structuring a product/project specification so that a genAI coding assistant can plan **and** implement in a single coherent flow — from requirements to working code with minimal iteration.

The key: your PRD becomes the prompt. If the PRD is genAI-friendly, the model can expand it into architecture, then code, then tests — all in one pass.

The output of one-shot planning is a **task spec**: a structured document that can be executed by an AI agent (or fed into a RALPH restart loop for longer tasks).

> Terminology note: this doc uses “GSD Task Spec” to mean “spec-first, Explore → Plan → Code → Commit.” It is not referring to a specific third-party “GSD” package/tooling.

See [GSD Task Spec Template](../reference/templates/gsd_task_spec.md) for the full template.

## Why it matters

**If you get this wrong:**
- AI generates fragmented, inconsistent code across files
- Requirements get lost between planning and implementation phases
- You spend more time iterating and fixing than you would have writing it yourself
- The model invents requirements you didn't specify

**If you get this right:**
- Single coherent implementation from spec to working code
- Requirements trace cleanly through every output
- Time-to-working-prototype dramatically reduced
- Iteration is refinement, not rescue

## How to apply it

### Step 1: Structure the PRD for AI consumption

Your PRD needs these elements, in this order:

| Element | What to include |
|---------|-----------------|
| **Problem** | What problem are we solving? Who has it? |
| **Success criteria** | Checkboxes the AI can verify against |
| **Scope** | What's in / what's out (explicit boundaries) |
| **Technical context** | Stack, existing patterns, constraints |
| **Expansion points** | Use "..." to mark where the AI should elaborate |

### Step 2: Use expansion markers

The `...` marker tells the AI: “You fill this in.” This is the genAI-friendly PRD secret.

```text
## API Endpoints

POST /users
- Validate input ...
- Create user in database ...
- Return created user with ID ...

GET /users/:id
- Fetch user by ID ...
- Handle not found ...
```

The model sees `...` and knows to expand each bullet into actual implementation.

### Additional steering keywords

Beyond `...`, use these information-dense keywords:
- `(mirror X)` — repeat the pattern from X
- `(similar to X)` — follow existing implementation X
- `(same pattern)` — continue the established pattern

Put instructions next to the code they govern. Each file is a “prompt surface.”

### Step 3: Include test commands

Always specify how to verify:

```text
## Test command
npm test

## Success criteria
- [ ] All tests pass
- [ ] GET /users/:id returns 200 for existing user
- [ ] POST /users validates email format
```

This gives the AI a concrete verification loop.

### Step 4: Request structured output

Ask for architecture **first**, then code:

```text
Before implementing, provide:
1. File structure (what files will be created)
2. Component breakdown (what each file does)
3. Implementation sequence (order of creation)
4. Integration points (how components connect)

Then implement in that order.
```

### Step 5: Provide guiding examples (optional)

If building something similar to an existing project, provide a **context pack** — a compressed reference implementation.

1. Take a high-quality reference repo
2. Compress into a single context file
3. Store in `ai_docs/` or `context/` directory
4. Reference in spec: “Use ai_docs/reference.txt as the guiding example”

LLMs perform better when pattern-matching against existing implementations.

## Project context files (optional)

Put stable project conventions and commands in a persistent context file that your code agent loads:

- Common patterns: `CONTEXT.md`, `PROJECT.md`, `.claude/CLAUDE.md`, `.cursor/rules.mdc`
- Keep it short; put fast-moving status/progress elsewhere
- Most agents walk up parent directories to find context files

## Autonomy earned by clarity

High-autonomy mode (fewer permission prompts, agentic execution) is safest after:
- Spec is complete (success criteria, test command, constraints)
- Guiding examples loaded (if applicable)
- Boundaries explicit (IN/OUT scope)

**Policy:** Autonomy is earned by upfront clarity.

### Operational note on permissions

If you want an unattended loop (for example, a RALPH-style restart loop), you need a permissions strategy. Common practice is to run in an isolated sandbox/repo and enable skip-permissions for the agent run; otherwise, permission prompts can break the loop.

## Expect 90-99%, then patch

First pass: 90-99% complete. Missing: edge cases, test gaps, wiring.

**Patching workflow:**
1. Run validation
2. Paste error back with minimal commentary
3. Re-run until green

This is normal — plan for refinement, not perfection on first pass.

## Signs you're doing it well

- First pass produces runnable code
- Code structure matches your PRD sections
- AI asks clarifying questions about real gaps (not basics)
- You can trace each feature back to a requirement
- Test command passes on first or second try

## Signs you're doing it wrong

- AI asks many clarifying questions mid-stream → PRD has gaps
- Output doesn't match requirements → Success criteria unclear
- Need to restart from scratch → Missing technical context
- Code is inconsistent across files → No expansion markers, AI guessed

## Quick reference

### Minimal one-shot PRD template

```text
# [Project Name]

## Problem
[Who has what problem? Why does it matter?]

## Success criteria
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

## Scope
IN: [what we're building]
OUT: [what we're NOT building]

## Technical context
- Stack: [language, framework, database]
- Patterns: [existing patterns to follow]
- Constraints: [performance, security, compatibility]

## Implementation

### [Component 1]
- [Requirement] ...
- [Requirement] ...

### [Component 2]
- [Requirement] ...

## Test command
[command to verify]
```

### One-shot prompt pattern

```text
I'm providing a PRD for one-shot implementation.

Rules:
1. Read the entire PRD first
2. Propose file structure before coding
3. Expand all "..." markers into implementation
4. Verify against success criteria checkboxes
5. Run test command and fix any failures

PRD:
"""
[paste PRD]
"""
```

### Checklist before one-shot

- [ ] Problem statement is concrete (not vague)
- [ ] Success criteria are checkboxes (testable)
- [ ] Scope explicitly says what's OUT
- [ ] Technical context includes stack and patterns
- [ ] Expansion markers (`...`) are used for implementation details
- [ ] Test command is specified

---

## Related

- [Context Engineering](context_engineering.md) — the underlying skill
- [GSD Task Spec Template](../reference/templates/gsd_task_spec.md) — the spec format this produces
- [GSD+RALPH Method](../playbooks/mle_gsd_ralph.md) — execution workflow for specs (RALPH restart loop)
- [Code Playbook](../playbooks/code.md) — general code patterns
