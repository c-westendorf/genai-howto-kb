---
title: Core Concepts
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)

# Core Concepts

These are the mental models that make genAI work effective. Internalize these, and the rest follows.

---

## [Context Engineering](context_engineering.md)

How you package input determines output quality. The prompt is the smallest part — what matters is role, task, constraints, inputs, format, and quality bar.

**Key insight**: More context isn't better context. Structured, relevant context is.

---

## [Explore → Select → Refine](explore_select_refine.md)

The thought partnership loop. Don't accept the first answer. Diverge (explore options), converge (select with criteria), iterate (refine to quality bar).

**Key insight**: The first answer is rarely the best answer. Make the model show you the option space first.

---

## [Trust Calibration](trust_calibration.md)

Match verification intensity to stakes. Low stakes = iterate fast. High stakes = demand evidence, cross-check, get expert review.

**Key insight**: Under-verifying high-stakes work is risky. Over-verifying low-stakes work is wasteful.

---

## [Parallel Execution](parallel_execution.md)

Scale thinking by running multiple threads. Branch-and-merge, generator-critic-editor, decompose-and-farm. When one perspective isn't enough.

**Key insight**: You can get multiple perspectives simultaneously and merge the best of each.

---

## [The Decision Flow](decision_flow.md)

The meta-question: What kind of task? What's at stake? What pattern fits? How much verification?

**Key insight**: Before you prompt, decide how you're going to work with the model on this task.

---

## [One-Shot Planning](oneshot_planning.md)

Structuring product/project specs so genAI can plan AND implement in a single flow. The PRD becomes the prompt — use `...` expansion markers to tell the AI where to fill in implementation details.

**Key insight**: The quality of your PRD determines whether one-shot works or wastes time.

---

## How these connect

```
Decision Flow (what pattern?)
    ↓
Context Engineering (package input)
    ↓
Explore → Select → Refine (execute the loop)
    ↓
Trust Calibration (verify proportionally)
    ↓
Parallel Execution (scale when needed)
```

Start with [Context Engineering](context_engineering.md) if you're new — it's the foundation everything else builds on.

---

## Related

- [Pitfalls & Fixes](../pitfalls/index.md) — when concepts go wrong
- [Playbooks](../playbooks/index.md) — concepts applied to tasks
- [Quick Reference](../reference/index.md) — prompts and templates
- [Glossary](../00_meta/glossary.md) — key terms defined
