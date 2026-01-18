---
title: Analysis & Decisions Playbook
updated: 2026-01-17
refs: [S0004]
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Writing](writing.md) · [Analysis](analysis.md) · [Research](research.md) · [Code](code.md) · [Meetings](meetings.md) · [DS Patterns](ds_patterns.md) · [MLE Patterns](mle_patterns.md) · [GSD+RALPH](mle_gsd_ralph.md) · [Business](business_patterns.md)

# Analysis & Decisions Playbook

## When to use this

- Comparing options and making recommendations
- Root cause analysis and diagnosis
- Decision memos and trade-off analysis
- Pre-mortems and risk assessment

---

## Context template

```text
Role: You are a [strategist / analyst / advisor] helping with [domain].

Task: Analyze [situation] and recommend [decision type].

Inputs:
"""
[Options to compare, data, constraints, requirements]
"""

Constraints:
- Decision criteria (ranked): [list priorities]
- Timeline: [when decision needed]
- Resources: [budget, people, time available]
- Risks to consider: [what could go wrong]

Format: [comparison table, memo, recommendation + rationale]

Quality bar:
- Trade-offs explicit
- Recommendation tied to criteria
- Risks identified with mitigations
```

---

## Prompt sequence

### 1. Explore: Surface options and criteria

```text
I need to decide: [decision]

Context: [situation]

Help me explore:
1. What are all the realistic options?
2. What criteria should I use to decide?
3. What am I not considering?
4. What would make this decision obvious?
```

### 2. Select: Structured comparison

```text
Compare these options: [list options]

Criteria (ranked by importance):
1. [criterion 1]
2. [criterion 2]
3. [criterion 3]

Return:
| Option | [C1] | [C2] | [C3] | Risks | Overall |

Then recommend one with rationale tied to criteria.
```

### 3. Refine: Stress-test the recommendation

```text
I'm leaning toward: [option]

Stress-test this:
1. What are 3 ways this could go wrong?
2. What am I not seeing?
3. What would make me regret this choice?
4. What's the backup plan if this fails?
```

---

## Verification checklist

Before finalizing:

- [ ] **All options considered**: Didn't miss obvious alternatives
- [ ] **Criteria explicit**: Decision tied to stated priorities
- [ ] **Trade-offs clear**: Know what you're giving up
- [ ] **Risks identified**: Top 3 risks with mitigations
- [ ] **Reversibility known**: How hard is it to change course
- [ ] **Next steps clear**: Know what happens after decision

---

## Common pitfalls

| Pitfall | Signs | Fix |
|---------|-------|-----|
| Hidden criteria | Decision doesn't match stated priorities | Make all criteria explicit |
| Optimism bias | Only upside considered | Run pre-mortem |
| False precision | Scores to decimal places | Use rough categories (high/med/low) |
| Missing options | Only comparing 2 things | Ask "what else could we do?" |
| Analysis paralysis | Can't decide, need more data | Set decision deadline, ask "what would make this obvious?" |

---

## Patterns

### Pattern: Options table

For structured comparison:

```text
Compare these options: [list]

Create a table:
| Option | Pros | Cons | Risks | Mitigations | Best when |

Criteria for comparison:
1. [priority 1]
2. [priority 2]
3. [priority 3]

Then recommend and explain why.
```

### Pattern: Pre-mortem

For risk identification:

```text
Assume this plan fails. It's 6 months later and it didn't work.

Write the post-mortem:
1. What went wrong? (10 possible reasons)
2. What were the warning signs we ignored?
3. What should we have done differently?

Then: Update the plan to address the top 3 risks.
```

### Pattern: Decision memo

For documenting decisions:

```text
Write a decision memo:

## Decision
[One sentence: what we're deciding to do]

## Context
[Why this decision is needed now]

## Options considered
[Brief description of each option]

## Recommendation
[Which option and why]

## Trade-offs
[What we're giving up]

## Risks and mitigations
[Top 3 risks and how we'll handle them]

## Next steps
[Immediate actions with owners]
```

### Pattern: Root cause analysis

For diagnosis:

```text
Problem: [symptom]

Help me find the root cause:
1. Ask "why" 5 times (5 Whys)
2. What are 3 possible root causes?
3. How would we test which one is correct?
4. What evidence would confirm/disconfirm each?
```

### Pattern: Break a tie

When options are too close:

```text
I can't decide between [A] and [B].

Help me break the tie:
1. What's the key differentiator?
2. What information would make the choice obvious?
3. If I had to decide in 5 minutes, which should I pick?
4. What's the cost of choosing wrong for each?
5. Which is more reversible?
```

---

## Related

- [Explore → Select → Refine](../concepts/explore_select_refine.md) — the decision loop
- [Select prompts](../reference/prompts/select.md) — selection prompts
- [Trust Calibration](../concepts/trust_calibration.md) — verification for decisions
