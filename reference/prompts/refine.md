---
title: Refine Prompts
updated: 2026-01-17
---

> **Navigation**: [START HERE](../../START_HERE.md) · [Concepts](../../concepts/index.md) · [Pitfalls](../../pitfalls/index.md) · [Decisions](../../decisions/index.md) · [Playbooks](../../playbooks/index.md) · [Reference](../index.md)
>
> **In this section**: [Explore](explore.md) · [Select](select.md) · [Refine](refine.md) · [Pushback](pushback.md) · [Verification](verification.md)

# Refine Prompts

Use these during the **refine phase** to iterate toward quality.

---

## Core refine prompt

```text
Here is the current draft: [paste]

Please:
1. Critique it against: clarity, correctness, completeness, usefulness
2. Identify the weakest part
3. Rewrite to a higher standard
4. Add a checklist I can use before shipping
```

---

## Targeted critique

```text
Review this: [paste]

Focus on: [specific aspect - e.g., "logic of the argument" or "clarity for non-technical readers"]

1. What's working?
2. What's not working?
3. Specific suggestions to improve
```

---

## Stress-test

```text
Here's my draft: [paste]

Stress-test it:
1. What are the 3 weakest points?
2. What would a skeptic attack?
3. What's missing that should be there?
4. What's there that shouldn't be?
```

---

## Polish for audience

```text
Here's my draft: [paste]

Audience: [who will read this]
Purpose: [what should they do/feel/understand after reading]

Rewrite to optimize for this audience and purpose.
Flag anything that doesn't serve them.
```

---

## Make it concrete

```text
This is too abstract: [paste]

Make it concrete:
1. Add specific examples
2. Replace vague terms with precise ones
3. Include edge cases
4. Add steps where needed
```

---

## Final check

```text
Before I ship this: [paste]

Final checklist:
1. Is it clear? (Can someone understand without asking questions?)
2. Is it correct? (Are claims accurate?)
3. Is it complete? (Are there gaps?)
4. Is it actionable? (Can someone use it?)

Flag any issues.
```

---

## The micro-loop

Repeat this sequence as needed:

```text
Draft → Critique → Edit → Verify

1. DRAFT: [current version]

2. CRITIQUE: What's wrong with this?

3. EDIT: Fix the issues you identified

4. VERIFY: Check the claims — are they grounded?
```

---

## When to use each

| Prompt | Use when |
|--------|----------|
| Core refine | Standard iteration |
| Targeted critique | Know what aspect to improve |
| Stress-test | Need to find weaknesses |
| Polish for audience | Draft is good but needs tailoring |
| Make it concrete | Too abstract or vague |
| Final check | About to ship |
| Micro-loop | Deep iteration needed |

---

## Stop conditions

Stop refining when:
- Output meets your quality bar
- Checklist passes
- Further iteration yields diminishing returns
- You've refined 3-4 times without major improvement

If still not right after 4+ iterations, see [Getting Stuck](../../pitfalls/getting_stuck.md).

---

## Related

- [Explore → Select → Refine](../../concepts/explore_select_refine.md) — the full loop
- [Select prompts](select.md) — previous phase
- [Output quality checklist](../checklists/output_quality.md) — what "done" looks like
