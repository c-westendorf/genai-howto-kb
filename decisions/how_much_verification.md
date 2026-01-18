---
title: How Much Verification Do I Need?
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Which Pattern](which_pattern.md) · [How Much Verification](how_much_verification.md) · [When to Stop](when_to_stop.md) · [Output Quality](output_quality.md) · [Start Over](start_over.md) · [Multi-LLM](multi_llm.md)

# How Much Verification Do I Need?

## Quick answer

Ask: **"If this is wrong, what breaks?"**

- **Internal draft, easily fixed** → Minimal (sanity check)
- **Shared with team/customers** → Moderate (check key claims)
- **High stakes, hard to reverse** → Full (evidence mapping, expert review)

## Decision criteria

### Minimal verification (TL1)

**Use when:**
- Output is internal only (won't be shared)
- Errors are easily caught and fixed
- Output is a draft you'll review anyway
- Speed matters more than perfection
- Task is low-stakes brainstorming

**What to do:**
- Quick read-through for obvious errors
- Check formatting is correct
- Basic sanity check ("does this make sense?")

**Time:** Seconds to minutes

### Moderate verification (TL2)

**Use when:**
- Output will be shared with team or customers
- Errors would cause rework or embarrassment
- Output contains factual claims others will rely on
- Task involves reasoning or recommendations

**What to do:**
- Identify 3-5 key claims
- Spot-check claims against sources
- Verify logic holds (premises → conclusion)
- Check internal consistency
- Have a human review before sharing

**Time:** 10-30 minutes depending on length

### Full verification (TL3)

**Use when:**
- Stakes are high (legal, financial, security, medical)
- Errors are hard to reverse
- Output will be published or drive major decisions
- Domain expertise is required to catch errors

**What to do:**
- List all factual claims
- Map each claim to authoritative source
- Independent verification (different source, different method)
- Domain expert review
- Create audit trail (prompt, output, verification steps)
- If can't verify → don't rely on model for decision

**Time:** Hours, depending on stakes

## Decision tree

```
Will this be published, sent to customers, or drive a major decision?
├── YES: Are the stakes high? (legal, financial, security, medical)
│   ├── YES → Full verification (TL3)
│   └── NO → Moderate verification (TL2)
└── NO: Is this an internal draft you'll review?
    ├── YES → Minimal verification (TL1)
    └── NO: Will someone else rely on this without reviewing?
        ├── YES → Moderate verification (TL2)
        └── NO → Minimal verification (TL1)
```

## Quick checklists

### Minimal (TL1)
- [ ] Read through once
- [ ] Check formatting
- [ ] Does it make sense?

### Moderate (TL2)
- [ ] Identify key claims (3-5)
- [ ] Spot-check against sources
- [ ] Verify logic holds
- [ ] Check internal consistency
- [ ] Human review before sharing

### Full (TL3)
- [ ] List all factual claims
- [ ] Map each to authoritative source
- [ ] Independent verification
- [ ] Domain expert review
- [ ] Create audit trail
- [ ] Document what was verified

## Common mistakes

| Mistake | Why it's bad | Fix |
|---------|--------------|-----|
| TL1 for customer docs | Errors reach customers | Use TL2 minimum |
| TL3 for brainstorming | Kills creativity, wastes time | Use TL1 |
| Skipping verification because "it looks right" | Hallucinations look right too | Verify key claims |
| Verifying with same model | Model won't catch own errors | Use external sources |

---

## Related

- [Trust Calibration](../concepts/trust_calibration.md) — the underlying concept
- [Verification checklist](../reference/checklists/verification.md) — detailed verification steps
- [Hallucinations](../pitfalls/hallucinations.md) — what you're checking for
