---
title: Explore Prompts
updated: 2026-01-17
---

> **Navigation**: [START HERE](../../START_HERE.md) · [Concepts](../../concepts/index.md) · [Pitfalls](../../pitfalls/index.md) · [Decisions](../../decisions/index.md) · [Playbooks](../../playbooks/index.md) · [Reference](../index.md)
>
> **In this section**: [Explore](explore.md) · [Select](select.md) · [Refine](refine.md) · [Pushback](pushback.md) · [Verification](verification.md)

# Explore Prompts

Use these during the **explore phase** to diverge and generate options.

---

## Core explore prompt

```text
Give me 5 meaningfully different approaches to [task].

For each approach:
- Brief description (1-2 sentences)
- Key strengths
- Key weaknesses
- When this approach would fail
```

---

## With clarifying questions

```text
You are my thought partner.

Task: [what I'm trying to accomplish]
Context: [relevant background]

Before proposing solutions:
1. Ask 5-10 clarifying questions (grouped by: goal, constraints, domain)
2. Then propose 3-5 different approaches
3. For each: pros, cons, and when it fails
4. Recommend which to try first and why
```

---

## Force divergence

```text
We need approaches that are maximally different from each other.

Give me 5 approaches:
1. The obvious approach
2. The opposite of #1
3. How a beginner would do this
4. How an expert in a different field would approach it
5. The approach that would work with unlimited resources
```

---

## Surface assumptions

```text
Before we solve this, help me find my blind spots.

For this task: [task]

1. What assumptions am I making?
2. Which assumptions are most likely wrong?
3. What constraints am I not seeing?
4. What would a skeptic challenge here?
```

---

## Identify risks

```text
For this task: [task]

What could go wrong?
1. Top 3 ways this could fail
2. Edge cases we might miss
3. Assumptions that could break
4. Dependencies that could cause problems
```

---

## Reframe the problem

```text
I've been thinking about this problem as: [current framing]

Give me 3 alternative framings:
1. A completely different way to see the problem
2. How a [different role/domain] would frame it
3. The version where we solve the root cause, not the symptom
```

---

## When to use each

| Prompt | Use when |
|--------|----------|
| Core explore | Starting fresh, need options |
| With clarifying questions | Unsure what you don't know |
| Force divergence | Options are too similar |
| Surface assumptions | Need to check blind spots |
| Identify risks | Planning something high-stakes |
| Reframe the problem | Stuck or exploring wrong problem |

---

## Related

- [Explore → Select → Refine](../../concepts/explore_select_refine.md) — the full loop
- [Select prompts](select.md) — next phase
- [Getting Stuck](../../pitfalls/getting_stuck.md) — when exploration isn't working
