---
title: When Do I Stop Refining?
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Which Pattern](which_pattern.md) · [How Much Verification](how_much_verification.md) · [When to Stop](when_to_stop.md) · [Output Quality](output_quality.md) · [Start Over](start_over.md) · [Multi-LLM](multi_llm.md)

# When Do I Stop Refining?

## Quick answer

- **Explore phase**: Stop when you have 3-5 meaningfully different approaches
- **Select phase**: Stop when one approach clearly wins on your criteria
- **Refine phase**: Stop when output meets quality bar and checklist passes

If you've iterated 4+ times without significant improvement, you're probably stuck — see [Getting Stuck](../pitfalls/getting_stuck.md).

## Stop conditions by phase

### Explore phase

**Continue if:**
- Options are too similar
- Obvious approaches are missing
- You haven't surfaced key trade-offs
- Clarifying questions revealed gaps you haven't filled

**Stop when:**
- You have 3-5 meaningfully different approaches
- Trade-offs between options are clear
- You understand what you'd need to know to choose
- Further exploration yields diminishing returns

**Check:**
- [ ] Options are actually different (not just rephrased)
- [ ] Pros/cons are specific, not generic
- [ ] You can explain the trade-off between top options

### Select phase

**Continue if:**
- Criteria aren't clear
- It's a tie between options
- You're not sure what you're optimizing for
- New information changed the picture

**Stop when:**
- One approach clearly wins on your priorities
- You can explain why you're choosing it
- You have success criteria (how you'll know it worked)
- You know the next concrete step

**Check:**
- [ ] Decision is tied to explicit criteria
- [ ] You can explain the trade-off you're making
- [ ] Success criteria are measurable
- [ ] First step is concrete and actionable

### Refine phase

**Continue if:**
- Output doesn't meet quality bar
- Specific weaknesses are identified
- Checklist has unchecked items
- Critique reveals fixable issues

**Stop when:**
- Quality bar is met
- Checklist passes
- Critique yields only minor suggestions
- Further iteration yields diminishing returns

**Check:**
- [ ] Meets all explicit requirements
- [ ] No major weaknesses in critique
- [ ] You'd be okay shipping this
- [ ] Last two iterations had small changes

## Quality bar checklist (universal)

- [ ] **Clear**: Someone can understand without asking questions
- [ ] **Correct**: Claims are accurate (at appropriate trust level)
- [ ] **Complete**: Covers what was asked, no obvious gaps
- [ ] **Actionable**: Can be used directly, not vague

## Warning signs: stop iterating

| Sign | What it means | What to do |
|------|---------------|------------|
| Same feedback twice | Not addressing root cause | Fix the actual problem, not symptoms |
| Iteration makes it worse | Context is polluted | Reset and start fresh |
| Changes are cosmetic | Reached quality ceiling | Accept and move on |
| 5+ iterations without progress | Stuck | See [Getting Stuck](../pitfalls/getting_stuck.md) |

## Decision tree

```
Has iteration made meaningful improvement?
├── YES: Has it met the quality bar?
│   ├── YES → Stop
│   └── NO → Continue refining
└── NO: How many iterations so far?
    ├── Less than 3 → Try a different angle
    └── 3+ → Consider starting over (see Getting Stuck)
```

---

## Related

- [Explore → Select → Refine](../concepts/explore_select_refine.md) — the full loop
- [Output quality](output_quality.md) — how to evaluate "good enough"
- [Start over?](start_over.md) — when to reset
- [Getting Stuck](../pitfalls/getting_stuck.md) — escape patterns
