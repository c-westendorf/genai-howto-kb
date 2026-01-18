---
title: Should I Start Over?
updated: 2026-01-17
---

# Should I Start Over?

## Quick answer

Start over if:
- You've iterated 5+ times without meaningful progress
- The model keeps returning to the same wrong answer
- You realized the framing was wrong from the start
- Accumulated context is making things worse

Don't start over if:
- You just need one more refinement
- The problem is specific and fixable
- Starting over would lose valuable work

## When to start over

### Yes, start over

**Context is poisoned:**
- Early wrong assumptions are baked in
- Model keeps referencing incorrect information
- Removing the poison would mean removing most of the context

**Wrong framing:**
- You're solving the wrong problem
- The approach was wrong from the start
- Refinement can't fix a wrong frame

**Stuck in a loop:**
- Same answer repeatedly despite different prompts
- 5+ iterations without meaningful improvement
- Each iteration makes it worse, not better

**Accumulated cruft:**
- Context has grown too large
- Conflicting instructions from different iterations
- Can't remember what's in the context anymore

### No, don't start over

**Specific, fixable problem:**
- You know exactly what's wrong
- Fix is localized, not systemic
- One more iteration should do it

**Would lose valuable work:**
- Good exploration already done
- Research/sources already gathered
- Just need to refine the selected approach

**Actually making progress:**
- Each iteration is better than the last
- You're converging on quality bar
- Just not done yet

## How to reset cleanly

### Option 1: New conversation, minimal context

Start fresh with only what's essential:

```text
[New conversation]

Task: [one sentence]
Key context: [minimal essentials]
Constraints: [only what's necessary]

Forget any previous attempts. What's the best approach?
```

### Option 2: Explicit reset in same conversation

```text
Let's reset completely. Ignore everything above this line.

The core goal is: [goal]
Here's what I know: [minimal facts]

Starting fresh, what would you do?
```

### Option 3: Reset with lessons learned

```text
Previous attempts haven't worked because: [why]

Starting fresh with this constraint:
- Don't do [what failed before]
- Instead try [different approach]

Task: [task]
```

## Decision tree

```
Have you iterated more than 4 times?
├── NO → Keep iterating, you're not stuck yet
└── YES → Is each iteration meaningfully better?
    ├── YES → Continue, you're converging
    └── NO → Is the problem the framing or the execution?
        ├── Framing → Start over with new frame
        └── Execution → Try one more targeted fix
            └── Still stuck? → Start over
```

## Signs you should have started over earlier

- "I should have done this differently from the start"
- You can't explain what's in your context anymore
- Model's answers reference things you don't remember adding
- It feels like pushing a boulder uphill

## Quick prompts

### To diagnose
```text
We've been iterating on this without progress.

1. What's the core problem we're trying to solve?
2. What approach have we been taking?
3. Why isn't it working?
4. What would we do differently if starting fresh?
```

### To reset with learnings
```text
Previous approach failed because: [reason]

What I want: [goal]
What I know now: [lessons learned]

Ignore everything before. What's a better approach?
```

### To salvage before resetting
```text
Before we reset, what's worth keeping from our work so far?
- Facts/research we gathered
- Approaches we ruled out (and why)
- Constraints we discovered
```

---

## Related

- [Getting Stuck](../pitfalls/getting_stuck.md) — escape patterns
- [When to stop refining?](when_to_stop.md) — stop conditions
- [Explore → Select → Refine](../concepts/explore_select_refine.md) — the loop
