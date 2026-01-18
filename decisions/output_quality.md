---
title: Is This Output Good Enough?
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Which Pattern](which_pattern.md) · [How Much Verification](how_much_verification.md) · [When to Stop](when_to_stop.md) · [Output Quality](output_quality.md) · [Start Over](start_over.md) · [Multi-LLM](multi_llm.md)

# Is This Output Good Enough?

## Quick answer

Check four dimensions:
1. **Grounded** — claims are supported, not fabricated
2. **Correct** — logic holds, no errors
3. **Complete** — covers what was asked, no gaps
4. **Actionable** — can be used directly, not vague

If all four pass at the appropriate trust level, it's good enough.

## The four dimensions

### 1. Grounded

Are the claims supported by evidence or provided context?

| Rating | What it means |
|--------|---------------|
| Poor | Claims appear fabricated or unsupported |
| Okay | Most claims seem reasonable but sources unclear |
| Good | Key claims are tied to provided context or cited sources |
| Excellent | All claims mapped to sources, uncertainty flagged |

**Quick check:**
- Can you trace each factual claim to a source?
- Are there claims that "sound right" but you can't verify?
- Does it make up specific details (names, numbers, dates)?

### 2. Correct

Does the logic hold? Are there errors?

| Rating | What it means |
|--------|---------------|
| Poor | Logic is flawed, conclusions don't follow |
| Okay | Logic is mostly sound, minor issues |
| Good | Logic is clear and valid |
| Excellent | Logic is rigorous, edge cases addressed |

**Quick check:**
- Do conclusions follow from premises?
- Are there logical leaps or hidden assumptions?
- Would a skeptic find obvious flaws?

### 3. Complete

Does it cover what was asked? Any gaps?

| Rating | What it means |
|--------|---------------|
| Poor | Missing major pieces of what was asked |
| Okay | Covers main points, some gaps |
| Good | Addresses the full task, no obvious gaps |
| Excellent | Comprehensive, includes edge cases |

**Quick check:**
- Does it answer the actual question?
- Are there obvious aspects not addressed?
- Would someone using this need to ask follow-up questions?

### 4. Actionable

Can someone use this directly?

| Rating | What it means |
|--------|---------------|
| Poor | Vague, can't act on it without significant work |
| Okay | General direction is clear, details missing |
| Good | Specific enough to act on |
| Excellent | Step-by-step, ready to use |

**Quick check:**
- If you handed this to someone, could they act on it?
- Are next steps clear?
- Are there concrete specifics or just generalities?

## Quality bar by trust level

| Trust Level | Grounded | Correct | Complete | Actionable |
|-------------|----------|---------|----------|------------|
| TL1 (Draft) | Okay | Okay | Okay | Okay |
| TL2 (Verified) | Good | Good | Good | Good |
| TL3 (Assured) | Excellent | Excellent | Excellent | Good |

## Quick evaluation prompt

```text
Rate this output:

1. Grounded (are claims supported?): 1-5
2. Correct (is logic sound?): 1-5
3. Complete (are there gaps?): 1-5
4. Actionable (can someone use this?): 1-5

For any score below 4:
- What's the specific problem?
- How would you fix it?
```

## Decision tree

```
Is it Grounded?
├── NO → Fix: demand sources, check claims
└── YES → Is it Correct?
    ├── NO → Fix: check logic, stress-test
    └── YES → Is it Complete?
        ├── NO → Fix: identify gaps, fill them
        └── YES → Is it Actionable?
            ├── NO → Fix: make concrete, add steps
            └── YES → Good enough ✓
```

## Common failure patterns

| Problem | Dimension failing | Quick fix |
|---------|-------------------|-----------|
| Sounds right but can't verify | Grounded | "List claims and sources" |
| Conclusion doesn't follow | Correct | "Check if conclusion follows from premises" |
| Answered something different | Complete | "Did you address [specific aspect]?" |
| Too vague to use | Actionable | "Make this concrete with specific steps" |

---

## Related

- [When to stop refining?](when_to_stop.md) — stop conditions
- [Trust Calibration](../concepts/trust_calibration.md) — what level is needed
- [Refine prompts](../reference/prompts/refine.md) — prompts to improve quality
- [Hallucinations](../pitfalls/hallucinations.md) — groundedness failures
