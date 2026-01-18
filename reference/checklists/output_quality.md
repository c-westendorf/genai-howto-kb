---
title: Output Quality Checklist
updated: 2026-01-17
---

> **Navigation**: [START HERE](../../START_HERE.md) · [Concepts](../../concepts/index.md) · [Pitfalls](../../pitfalls/index.md) · [Decisions](../../decisions/index.md) · [Playbooks](../../playbooks/index.md) · [Reference](../index.md)
>
> **In this section**: [Context Pack](context_pack.md) · [Verification](verification.md) · [Output Quality](output_quality.md) · [Security](security.md)

# Output Quality Checklist

Quick quality assessment for genAI outputs. Use to decide: accept, refine, or reject.

---

## The four dimensions

Every output should be evaluated on:

1. **Grounded** — Based on real information, not fabricated
2. **Correct** — Accurate and logically sound
3. **Complete** — Covers what was asked, nothing important missing
4. **Actionable** — Useful for your actual purpose

---

## Quick quality check (2 minutes)

Use for low-stakes outputs or first-pass triage.

| Dimension | Quick check | Pass? |
|-----------|-------------|-------|
| Grounded | Do claims seem based on real info (not made up)? | ☐ |
| Correct | Any obvious errors, contradictions, or nonsense? | ☐ |
| Complete | Does it address what I asked? | ☐ |
| Actionable | Can I use this for my purpose? | ☐ |

**Result**:
- All pass → Accept or light refine
- 1-2 fail → Refine with specific feedback
- 3+ fail → Reject, restart with better context

---

## Detailed quality check (10-15 minutes)

Use for medium-stakes outputs or when quick check raises concerns.

### Grounded

- [ ] **Claims sourced**: Key claims have basis in provided context or verifiable facts
- [ ] **No fabrication**: Nothing appears made up (fake citations, invented statistics)
- [ ] **Appropriate certainty**: Confidence matches evidence strength
- [ ] **Speculation labeled**: Uncertain claims marked as such

**Red flags**:
- Highly specific numbers without sources
- "According to [source]" you can't verify
- Confident tone without evidence
- Details that are too perfect

### Correct

- [ ] **Factually accurate**: Verifiable facts are correct
- [ ] **Logically sound**: Reasoning follows, conclusions supported
- [ ] **Internally consistent**: No contradictions within the output
- [ ] **Contextually appropriate**: Fits with what you know to be true

**Red flags**:
- Statements that contradict your domain knowledge
- Logical leaps without justification
- Inconsistencies between sections
- Wrong terminology or misapplied concepts

### Complete

- [ ] **Addresses the ask**: Covers what was requested
- [ ] **Key points included**: Nothing important missing
- [ ] **Appropriate depth**: Right level of detail for purpose
- [ ] **Edge cases considered**: Obvious exceptions handled

**Red flags**:
- Glaring omissions
- Surface-level when depth needed
- Missing obvious considerations
- Avoiding difficult parts of the question

### Actionable

- [ ] **Fits purpose**: Can actually use this for intended goal
- [ ] **Specific enough**: Not too vague to act on
- [ ] **Appropriate format**: Structure works for your use
- [ ] **Next steps clear**: If action-oriented, actions are concrete

**Red flags**:
- Too generic to be useful
- Theoretically correct but practically useless
- Wrong format for your need
- "Consider..." without specifics

---

## Quality by output type

### Analysis / Recommendations

| Quality check | What to look for |
|---------------|------------------|
| Grounded | Recommendations tied to evidence, not opinion presented as fact |
| Correct | Logic sound, alternatives fairly compared, trade-offs accurate |
| Complete | Options covered, criteria explicit, risks addressed |
| Actionable | Clear recommendation, specific next steps, decision-ready |

### Written content

| Quality check | What to look for |
|---------------|------------------|
| Grounded | Facts accurate, claims supportable, no made-up quotes |
| Correct | Grammar correct, logic flows, structure sound |
| Complete | Covers topic, appropriate length, nothing critical missing |
| Actionable | Fits purpose, right tone/audience, usable as-is or with minor edits |

### Code

| Quality check | What to look for |
|---------------|------------------|
| Grounded | Uses real APIs, correct syntax, exists in language/framework |
| Correct | Compiles/runs, produces expected output, handles errors |
| Complete | All requirements addressed, edge cases handled |
| Actionable | Integrates with codebase, maintainable, production-ready |

### Research / Summaries

| Quality check | What to look for |
|---------------|------------------|
| Grounded | Based on sources provided, citations accurate |
| Correct | Accurately represents source material, no distortion |
| Complete | Key points captured, appropriate depth |
| Actionable | Answers the question, organized usefully, can act on insights |

---

## Scoring rubric

For formal assessment, score each dimension:

| Score | Meaning |
|-------|---------|
| 3 | Strong — Fully meets criteria, no concerns |
| 2 | Adequate — Meets criteria with minor issues |
| 1 | Weak — Significant gaps or concerns |
| 0 | Failing — Does not meet criteria |

**Total score interpretation**:
- 10-12: Accept with confidence
- 7-9: Accept with light refinement
- 4-6: Significant refinement needed
- 0-3: Reject and restart

---

## Decision tree

```
Start
  │
  ▼
[Quick check: Any obvious failures?]
  │
  ├── Yes → [Which dimensions?]
  │           │
  │           ├── Grounded/Correct → High risk. Verify carefully or reject.
  │           │
  │           └── Complete/Actionable → Refine with specific asks.
  │
  └── No → [Detailed check for stakes level]
            │
            ├── Low stakes → Accept
            │
            ├── Medium stakes → Verify key claims, then accept
            │
            └── High stakes → Full verification, expert review
```

---

## Refinement prompts by dimension

### If not grounded

```text
I'm concerned about grounding. For each claim in your response:
1. What's the source or basis?
2. What's your confidence level?
3. Mark anything uncertain as [UNVERIFIED]
```

### If not correct

```text
I found potential issues with [specific problem].
Please verify:
1. Is [specific claim] accurate?
2. Walk me through your reasoning for [conclusion]
3. Are there contradictions I should be aware of?
```

### If not complete

```text
This is missing [specific gap]. Please add:
1. [Missing element 1]
2. [Missing element 2]

Also check: What else might be missing that I haven't noticed?
```

### If not actionable

```text
This is too [vague/generic/theoretical]. Make it actionable:
1. Give specific examples
2. Provide concrete next steps
3. Remove hedging where you can commit
```

---

## Related

- [Verification Checklist](verification.md) — detailed verification process
- [Output Quality (Decisions)](../../decisions/output_quality.md) — when output is good enough
- [When to Stop](../../decisions/when_to_stop.md) — stop conditions
