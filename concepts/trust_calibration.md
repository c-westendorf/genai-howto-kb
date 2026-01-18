---
title: Trust Calibration
updated: 2026-01-17
refs: [S0023, S0003, S0004]
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Context Engineering](context_engineering.md) · [Explore → Select → Refine](explore_select_refine.md) · [Trust Calibration](trust_calibration.md) · [Parallel Execution](parallel_execution.md) · [Decision Flow](decision_flow.md) · [One-Shot Planning](oneshot_planning.md)

# Trust Calibration

## What it is

Matching your verification intensity to the stakes. Low stakes = iterate fast. High stakes = demand evidence, cross-check, get expert review.

The question isn't "is the model right?" but:
- **How confident do we need to be?**
- **What happens if we're wrong?**

## Why it matters

**If you under-verify high-stakes work:**
- Hallucinations become published facts
- Wrong conclusions drive bad decisions
- Errors surface late, when they're expensive to fix

**If you over-verify low-stakes work:**
- You waste time checking things that don't matter
- Iteration slows to a crawl
- You treat brainstorming like legal review

**Right-sizing trust means:**
- Fast iteration when stakes are low
- Rigorous checking when stakes are high
- Conscious decisions about which mode you're in

## How to apply it

### Step 1: Assess the stakes

Ask: **"If this is wrong, what breaks?"**

| Stakes | Examples | Consequence of error |
|--------|----------|---------------------|
| **Low** | Brainstorming, internal drafts, exploration | Minor rework, no external impact |
| **Medium** | Shared docs, team decisions, customer-facing | Rework + reputation risk, but recoverable |
| **High** | Legal, financial, security, medical, public | Serious harm, hard to reverse |

### Step 2: Choose your trust level

| Level | When to use | What it means |
|-------|-------------|---------------|
| **TL0 — Brainstorm only** | High-stakes domain, no ground truth | Use for ideas only. Verify everything externally. |
| **TL1 — Draft trust** | Low stakes, reversible | Light review. Check for obvious errors. |
| **TL2 — Verified trust** | Medium stakes, will be shared/acted on | Check key claims. Demand citations. Review logic. |
| **TL3 — Assured trust** | High stakes, hard to reverse | Full verification. Authoritative sources. Expert signoff. Audit trail. |

### Step 3: Apply appropriate controls

**TL1 (Draft trust):**
- Formatting constraints
- Basic sanity check
- Quick read-through

**TL2 (Verified trust):**
- List all factual claims
- Demand citations with links
- Check internal consistency
- Cross-check 2-3 key claims
- Human review before sharing

**TL3 (Assured trust):**
- Authoritative sources only (standards, peer-reviewed, government)
- Independent verification (different model, different source)
- Expert signoff in domain
- Audit trail (prompt, output, verification steps)
- If can't verify → don't rely on model for decision

### Step 4: Watch for trust miscalibration

Common mistakes:
- **Treating brainstorming as TL2** → Wastes time, kills creativity
- **Treating customer docs as TL1** → Errors reach customers
- **Assuming TL3 is possible** → Sometimes you can't verify; use model for ideas only

See [Trust Miscalibration](../pitfalls/trust_miscalibration.md).

## Signs you're doing it well

- You consciously choose a trust level before starting
- Low-stakes work moves fast
- High-stakes work has documented verification
- You can explain your verification choices to others

## Signs you're doing it wrong

- Everything gets the same level of scrutiny → You're not calibrating
- You publish without checking → Under-verification
- Brainstorming takes hours → Over-verification
- You're surprised by errors late → Stakes assessment was wrong

## Quick reference

### Stakes assessment prompt
```text
If this output is wrong, what breaks?
- Who is affected?
- How hard is it to fix?
- What's the worst case?

Based on this, should we treat this as low/medium/high stakes?
```

### Verification prompt (TL2)
```text
List every factual claim in your response.
For each claim:
- Confidence: high/medium/low
- Source: where this comes from
- Flag: any uncertainty

Which claims should I verify before using this?
```

### Trust level decision tree

```
Is this high-stakes? (legal, financial, security, medical, public)
  → YES → TL3: Full verification, expert signoff
  → NO ↓

Will this be shared or acted on?
  → YES → TL2: Verify key claims, human review
  → NO ↓

Is this reversible/internal?
  → YES → TL1: Light review, iterate fast
```

## Common failure modes by task type

| Task type | What goes wrong | How to catch it |
|-----------|-----------------|-----------------|
| Transform (summarize, extract) | Omissions, subtle meaning drift | Compare to source |
| Reason/decide | Confident wrong conclusions | Check logic, test assumptions |
| Compute (math, code) | Arithmetic/logic errors, edge cases | Run the code, verify math |
| Research | Hallucinated citations, outdated facts | Click every link, cross-check dates |

---

## Sources

Concepts in this guide are grounded in research and best practices:

- [S0001: Survey of Hallucination in NLG](../90_sources/extraction_cards/S0001_survey_hallucination_nlg.md) — hallucination taxonomy, why verification matters
- [S0003: TruthfulQA](../90_sources/extraction_cards/S0003_truthfulqa.md) — truthfulness benchmarks
- [S0004: HELM](../90_sources/extraction_cards/S0004_helm.md) — calibration and evaluation metrics
- [S0006: LMs Mostly Know What They Know](../90_sources/extraction_cards/S0006_lm_mostly_know_what_they_know.md) — model calibration

---

## Related

- [Hallucinations](../pitfalls/hallucinations.md) — what trust calibration guards against
- [Trust Miscalibration](../pitfalls/trust_miscalibration.md) — when you get trust wrong
- [Verification Checklist](../reference/checklists/verification.md) — TL1/TL2/TL3 checklists
- [How Much Verification?](../decisions/how_much_verification.md) — decision support
