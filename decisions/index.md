---
title: Decision Support
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)

# Decision Support

Quick answers to common questions about what to do next. Each decision includes a quick answer, decision criteria, and examples.

---

## [What pattern should I use?](which_pattern.md)

Single-shot vs. thought partnership vs. parallel execution.

**Quick answer**:
- Simple, low-stakes, well-defined → Single-shot
- Complex, needs exploration → Thought partnership (explore/select/refine)
- Very complex, needs breadth → Parallel execution

---

## [How much verification do I need?](how_much_verification.md)

Trust level selection based on stakes, reversibility, and audience.

**Quick answer**:
- Internal draft, easily fixed → Minimal (sanity check)
- Shared with team/customers → Moderate (check key claims)
- High stakes, hard to reverse → Full (evidence mapping, expert review)

---

## [When do I stop refining?](when_to_stop.md)

Stop conditions for explore, select, and refine phases.

**Quick answer**:
- **Explore**: Stop when you have 3-5 meaningfully different approaches
- **Select**: Stop when one approach clearly wins on your criteria
- **Refine**: Stop when output meets quality bar and checklist passes

---

## [Is this output good enough?](output_quality.md)

Quick quality rubric for evaluating genAI output.

**Quick answer**: Check four dimensions:
1. **Grounded** — claims are supported, not fabricated
2. **Correct** — logic holds, no errors
3. **Complete** — covers what was asked, no gaps
4. **Actionable** — can be used directly, not vague

---

## [Should I start over?](start_over.md)

When iteration is wasteful and a reset is better.

**Quick answer**: Start over if:
- You've iterated 5+ times without progress
- The model keeps returning to the same wrong answer
- You realize the framing was wrong from the start

---

## [When to use multiple models?](multi_llm.md)

Model selection and multi-LLM tactics for verification and escaping stuck states.

**Quick answer**:
- **Triangulation** — compare answers across models for high-stakes verification
- **Fresh perspective** — try a different model when stuck
- **Match to task** — use models' strengths (coding, creativity, analysis)

---

## When to use this section

Come here when you're at a decision point and not sure what to do next. These are the questions people ask most often.

For deeper understanding, see [Core Concepts](../concepts/index.md).
For when things go wrong, see [Pitfalls & Fixes](../pitfalls/index.md).
