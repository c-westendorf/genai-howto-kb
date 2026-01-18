---
title: Verification Checklist
updated: 2026-01-17
---

# Verification Checklist

Use this checklist to verify genAI outputs before using them. Match intensity to trust level.

---

## Quick verification (TL1 — Low stakes)

Minimum check for drafts, brainstorms, internal explorations.

- [ ] **Plausibility check**: Does this make sense?
- [ ] **Obvious errors**: Any glaring mistakes, typos, contradictions?
- [ ] **Fits purpose**: Does it answer what I asked?
- [ ] **Safe to iterate**: Can I refine this without harm if wrong?

**Time**: 30 seconds to 2 minutes

---

## Standard verification (TL2 — Medium stakes)

For work that will be shared, decisions that matter, external-facing content.

### Accuracy
- [ ] **Claims grounded**: Key claims have basis (provided context or verifiable)
- [ ] **Numbers verified**: Any statistics, dates, figures checked against source
- [ ] **Names correct**: People, companies, products spelled correctly
- [ ] **No fabrication**: Nothing made up that sounds plausible

### Completeness
- [ ] **Addresses the ask**: Covers what was requested
- [ ] **Key points included**: Nothing important missing
- [ ] **Edge cases considered**: Obvious edge cases handled

### Consistency
- [ ] **Internally consistent**: No contradictions within output
- [ ] **Matches context**: Aligns with provided information
- [ ] **Tone appropriate**: Right style for audience

### Actionability
- [ ] **Clear next steps**: If action-oriented, actions are specific
- [ ] **Implementable**: Recommendations are feasible
- [ ] **Decisions clear**: If decision-focused, decision is unambiguous

**Time**: 5-15 minutes

---

## Rigorous verification (TL3 — High stakes)

For public claims, legal/compliance, high-cost decisions, safety-critical.

### All of TL2, plus:

### Source verification
- [ ] **Sources cited**: Claims have explicit sources
- [ ] **Sources checked**: I've verified sources exist and say what's claimed
- [ ] **Sources authoritative**: Sources are credible for these claims
- [ ] **Recency verified**: Information is current enough for purpose

### Logic verification
- [ ] **Reasoning sound**: Arguments follow logically
- [ ] **Assumptions explicit**: Underlying assumptions are stated
- [ ] **Alternatives considered**: Other interpretations addressed
- [ ] **Limitations acknowledged**: What this doesn't tell us is clear

### Expert verification
- [ ] **Domain expert reviewed**: Someone with expertise has checked
- [ ] **Cross-checked**: Verified against independent source
- [ ] **Stress-tested**: Tried to break the reasoning

### Risk verification
- [ ] **Failure modes identified**: What could go wrong
- [ ] **Reversibility assessed**: Can we undo if wrong
- [ ] **Worst case acceptable**: Comfortable with worst outcome

**Time**: 30+ minutes, potentially hours for critical work

---

## Verification by output type

### For factual claims
- [ ] Can I trace this to a source?
- [ ] Is the source authoritative?
- [ ] Is the information current?
- [ ] Has this been cross-referenced?

### For code
- [ ] Have I read and understood it?
- [ ] Have I tested with normal inputs?
- [ ] Have I tested edge cases (empty, null, boundary)?
- [ ] Have I checked for security issues?
- [ ] Does it integrate with surrounding code?

### For recommendations
- [ ] Is the reasoning explicit?
- [ ] Are alternatives fairly represented?
- [ ] Are trade-offs acknowledged?
- [ ] Does it match my constraints?

### For summaries
- [ ] Does it capture key points from source?
- [ ] Is anything important missing?
- [ ] Any distortion of original meaning?
- [ ] Appropriate level of detail?

### For creative content
- [ ] Does it match the brief?
- [ ] Is the tone right?
- [ ] Any inappropriate content?
- [ ] Original enough (not too generic)?

---

## Red flags requiring extra verification

Stop and verify more carefully if you see:

| Red flag | Why it matters | What to do |
|----------|----------------|------------|
| Highly specific numbers | Specificity signals confidence but may be fabricated | Verify every number against source |
| Confident assertions | Confidence ≠ accuracy | Ask for evidence |
| Claims about recent events | Training data may be stale | Verify with current sources |
| Legal/medical/financial advice | High-stakes domains | Get expert review |
| URLs or citations | Often hallucinated | Check every link |
| "According to..." | May be fabricating sources | Verify the source exists and says this |
| Technical details | Plausible-sounding but potentially wrong | Test or verify with docs |

---

## Verification prompts

Use these to help verify:

### Ask for evidence
```text
For each claim in your response, list:
1. The claim
2. The evidence or source
3. Your confidence level (high/medium/low)
4. What would change your assessment
```

### Check for gaps
```text
What did you NOT include that might be relevant?
What assumptions are you making?
What would a skeptic challenge?
```

### Stress-test
```text
Try to find holes in your own response.
What's the strongest argument against this?
Where might you be wrong?
```

---

## After verification fails

If verification reveals problems:

1. **Minor issues**: Refine with specific corrections
2. **Significant gaps**: Ask for revision with explicit requirements
3. **Fundamental problems**: Start over with better context
4. **Trust breakdown**: Reduce scope, increase human involvement

---

## Related

- [Trust Calibration](../../concepts/trust_calibration.md) — matching verification to stakes
- [Hallucinations](../../pitfalls/hallucinations.md) — what to watch for
- [Verification Prompts](../prompts/verification.md) — prompts to use during verification
