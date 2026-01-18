---
title: Verification Prompts
updated: 2026-01-17
---

# Verification Prompts

Prompts to verify genAI outputs. Use after generation, before trusting.

---

## Evidence and sourcing

### Demand evidence for claims

```text
For each factual claim in your response:
1. State the claim
2. Provide the evidence or source
3. Rate your confidence: high (I'm certain) / medium (likely but verify) / low (uncertain)
4. Note if this should be independently verified
```

### Separate facts from inferences

```text
In your response, separate:
1. **Facts**: Things that are verifiably true
2. **Inferences**: Conclusions drawn from facts
3. **Speculation**: Things that might be true but aren't verified
4. **Assumptions**: Things you're taking as given

Label each statement accordingly.
```

### Check for fabrication

```text
Review your response for anything that might be fabricated:
- Specific statistics or numbers
- Quotes or citations
- Dates or timelines
- Names of people, companies, or products
- Technical specifications

For each, either provide the source or mark as [UNVERIFIED].
```

---

## Logic and reasoning

### Expose reasoning

```text
Show your reasoning step by step:
1. What information did you start with?
2. What inferences did you make?
3. What led you to this conclusion?
4. Where might your reasoning be wrong?
```

### Challenge assumptions

```text
What assumptions are you making in this response?
For each assumption:
1. State the assumption
2. Explain why you made it
3. What would change if this assumption is wrong?
```

### Find weaknesses

```text
Be a critic of your own response:
1. What's the weakest part of this argument?
2. What evidence would contradict this?
3. What alternative explanation exists?
4. What am I missing?
```

### Steel-man alternatives

```text
Present the strongest possible argument against your recommendation.
Don't straw-man it — give it the best case.
Then explain why you still hold your position (or acknowledge if this changes your view).
```

---

## Completeness

### Check for gaps

```text
What did you NOT include that might be relevant?
- Topics you skipped
- Perspectives you didn't represent
- Edge cases you didn't address
- Caveats you didn't mention
```

### Verify coverage

```text
Check your response against the original request:
1. What was asked for?
2. What did you provide?
3. What's missing?
4. What did you add that wasn't asked for?
```

### Edge case review

```text
What edge cases might break this?
- Unusual inputs
- Boundary conditions
- Error scenarios
- Unexpected user behavior
```

---

## Accuracy checks

### Cross-reference

```text
If I were to verify this against [specific source/authority], what might I find that contradicts what you said?
```

### Version check

```text
This information might change over time.
1. When might this information become outdated?
2. What should I verify is still current?
3. What's the date of the information you're drawing on?
```

### Domain validation

```text
If a domain expert reviewed this, what would they likely:
1. Agree with?
2. Push back on?
3. Add nuance to?
4. Correct outright?
```

---

## Output-specific verification

### For code

```text
Review this code for:
1. **Correctness**: Does it do what it's supposed to?
2. **Edge cases**: What inputs would break it?
3. **Security**: Any vulnerabilities (injection, validation, secrets)?
4. **Integration**: Will it work with surrounding code?

For each issue found, rate severity (critical/medium/low).
```

### For recommendations

```text
Verify this recommendation:
1. **Criteria used**: What factors determined this choice?
2. **Alternatives rejected**: Why not the other options?
3. **Trade-offs accepted**: What am I giving up?
4. **Assumptions made**: What must be true for this to work?
5. **Failure modes**: How could this recommendation fail?
```

### For summaries

```text
Verify this summary against the source:
1. **Key points captured**: Nothing important missing?
2. **Accuracy**: Any distortion of the original meaning?
3. **Emphasis**: Right things prioritized?
4. **Omissions**: Anything left out that matters?
```

### For analysis

```text
Verify this analysis:
1. **Data grounding**: What data supports each conclusion?
2. **Logical flow**: Does each step follow from the previous?
3. **Alternative interpretations**: What else could explain this?
4. **Confidence calibration**: How certain should I be?
```

---

## Trust calibration prompts

### For low-stakes (TL1)

```text
Quick check: Is there anything obviously wrong with this?
Any red flags I should investigate further?
```

### For medium-stakes (TL2)

```text
Before I use this:
1. What should I verify independently?
2. What could go wrong if something is inaccurate?
3. What's your confidence level?
```

### For high-stakes (TL3)

```text
This is high-stakes. I need:
1. Sources for every factual claim
2. Explicit confidence levels
3. Known limitations and uncertainties
4. What an expert might disagree with
5. What I should independently verify before proceeding
```

---

## Meta-verification

### Ask about confidence

```text
How confident are you in this response?
- What parts are you most certain about?
- What parts are you least certain about?
- What would increase your confidence?
- What would make you change your answer?
```

### Ask what you don't know

```text
What don't you know that would be relevant here?
What information would help you give a better answer?
What are you uncertain about?
```

### Ask for failure modes

```text
How might this response be wrong?
- Factually incorrect
- Logically flawed
- Missing important context
- Outdated
- Biased in some way
```

---

## Related

- [Verification Checklist](../checklists/verification.md) — structured verification process
- [Pushback Prompts](pushback.md) — challenging during generation
- [Trust Calibration](../../concepts/trust_calibration.md) — matching effort to stakes
