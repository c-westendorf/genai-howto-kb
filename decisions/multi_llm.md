---
title: Multi-LLM Tactics
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Which Pattern](which_pattern.md) · [How Much Verification](how_much_verification.md) · [When to Stop](when_to_stop.md) · [Output Quality](output_quality.md) · [Start Over](start_over.md) · [Multi-LLM](multi_llm.md)

# Multi-LLM Tactics

## Quick answer

Use multiple models when:
- You need to triangulate on truth (high-stakes verification)
- You're stuck and need a fresh perspective
- You want to compare reasoning approaches
- One model's weakness is another's strength

## When to use multiple models

### For verification (high-stakes)

Run the same query through 2-3 models and compare:

```text
[Same prompt to Model A, Model B, Model C]

Then ask yourself:
- Where do they agree? (Higher confidence)
- Where do they disagree? (Needs verification)
- What does each model add that others miss?
```

**Best for:** Factual claims, analysis, recommendations where errors are costly.

### For getting unstuck

When one model keeps giving the same unsatisfactory answer:

1. Take your best checkpoint from Model A
2. Start fresh with Model B
3. Compare approaches

Different models have different:
- Training data and knowledge cutoffs
- Reasoning patterns
- Failure modes
- Strengths (coding, writing, analysis, creativity)

**Best for:** When stuck in a loop, context is poisoned, or need fresh framing.

### For parallel exploration

Use models in parallel during the Explore phase:

```text
Model A: Give me 3 approaches to [task]
Model B: Give me 3 approaches to [task]
Model C: Give me 3 approaches to [task]

Then: Combine best ideas, run Select phase with preferred model
```

**Best for:** Creative work, brainstorming, when you want maximum divergence.

### For specialized tasks

Match model to task type:

| Task type | Consider |
|-----------|----------|
| Code generation | Models with strong coding benchmarks |
| Creative writing | Models known for style and creativity |
| Factual research | Models with recent knowledge, citation ability |
| Long-form analysis | Models with large context windows |
| Fast iteration | Smaller/faster models for drafts |

## Model selection criteria

### Know your models' strengths

Before choosing, consider:

| Dimension | Questions to ask |
|-----------|-----------------|
| **Knowledge cutoff** | When was training data collected? Current enough for your task? |
| **Reasoning** | Strong at logic, math, multi-step problems? |
| **Creativity** | Good at divergent thinking, style, originality? |
| **Coding** | Accurate syntax, good debugging, knows your stack? |
| **Following instructions** | Sticks to format, constraints, length requirements? |
| **Context window** | Can it handle your full context? |
| **Speed/cost** | Fast enough for iteration? Affordable for your volume? |

### When models disagree

If models give different answers:

1. **Check for factual claims** — verify with external sources
2. **Look at reasoning** — which logic is more sound?
3. **Consider the stakes** — if high-stakes, default to most conservative
4. **Ask each to critique the other** — surface the disagreement explicitly

```text
Model A said: [A's answer]
Model B said: [B's answer]

What are the key differences? Which reasoning is more sound? What would resolve the disagreement?
```

## Multi-model patterns

### Pattern: Triangulation

For high-stakes factual work:

```
Query → Model A → Answer A
Query → Model B → Answer B
Query → Model C → Answer C
         ↓
    Compare answers
         ↓
    Where they agree = higher confidence
    Where they disagree = verify externally
```

### Pattern: Generator + Critic (different models)

One model generates, another critiques:

```
Model A (Generator): Create [output]
         ↓
Model B (Critic): Review for errors, gaps, weaknesses
         ↓
Model A or C (Editor): Revise based on critique
```

**Why different models:** The critic has no investment in the original answer.

### Pattern: Checkpoint migration

When stuck, migrate your best work to a fresh model:

```
Model A: [work until stuck]
         ↓
    Create checkpoint (goal, learnings, research)
         ↓
Model B: [Start fresh with checkpoint]
         ↓
    Compare Model B's approach to Model A's
```

### Pattern: Ensemble voting

For classification or decision tasks:

```
Model A: Recommends Option X
Model B: Recommends Option Y
Model C: Recommends Option X
         ↓
    Majority: Option X (but investigate why B disagreed)
```

## When NOT to use multiple models

- **Low-stakes work** — overhead isn't worth it
- **Simple tasks** — one model is sufficient
- **You trust the model** — no need to verify everything
- **Speed is critical** — parallel models slow you down
- **Context is specialized** — you've built up valuable context in one model

## Quick prompts

### To compare reasoning

```text
I got this answer from another model: [paste answer]

Do you agree? Where do you disagree and why?
What would you add or change?
```

### To migrate checkpoints

```text
I've been working on [task] in another conversation.

What we learned:
- Goal: [refined goal]
- Failed approaches: [what didn't work]
- Useful findings: [research, facts]

Starting fresh, what's your recommended approach?
```

### To triangulate

```text
After getting answers from multiple models:

Model A said: [summary]
Model B said: [summary]

Where do they agree?
Where do they disagree?
What evidence would resolve the disagreement?
```

---

## Related

- [Getting Stuck](../pitfalls/getting_stuck.md) — when to try a different model
- [Parallel Execution](../concepts/parallel_execution.md) — running multiple threads
- [Trust Calibration](../concepts/trust_calibration.md) — verification through triangulation
- [Should I Start Over?](start_over.md) — checkpoint migration
