---
title: Hallucination Traps
updated: 2026-01-17
refs: [S0001, S0003]
---

# Hallucination Traps

## What it looks like

- Output sounds confident but claims are false
- Citations look plausible but don't exist
- Numbers are specific but made up
- Names, dates, or events are fabricated
- Each sentence is plausible, but the whole answer is wrong

## Why it happens

1. **Models predict plausible text, not truth**: They're trained to generate what sounds right, not what is right.

2. **No ground truth access**: Without access to sources, the model fills gaps with plausible-sounding content.

3. **Confidence isn't calibrated**: Models express certainty regardless of actual accuracy.

4. **You didn't ask for uncertainty**: Without explicit prompting, models don't flag what they don't know.

5. **The question invites fabrication**: Asking for specific facts the model doesn't know forces it to invent.

## Types of hallucination

| Type | What it is | Example |
|------|-----------|---------|
| **Fabrication** | Invents facts, names, numbers | "According to a 2023 study by Dr. Smith..." (doesn't exist) |
| **False specificity** | Adds fake precision | "The market grew 23.7% in Q3" (number made up) |
| **Conflation** | Merges distinct things | Combines two people or events into one |
| **Outdatedness** | Correct historically, wrong now | "The CEO is [previous CEO]" |
| **Citation hallucination** | Invents sources | Plausible URLs, titles, authors that don't exist |

## How to fix it

### Quick fix

Ask: "List the factual claims you just made. For each, rate your confidence (high/medium/low) and flag any uncertainty."

Then verify the low-confidence claims externally.

### Full fix

1. **Demand claims, not prose**
   ```text
   Before writing, list the key factual claims you'll include.
   For each claim, note whether it's:
   - From the context I provided (cite the section)
   - From your training data (flag as "training data")
   - Uncertain (flag as "uncertain")
   ```

2. **Require sources with mapping**
   ```text
   For each claim, provide:
   - The source (title, URL if applicable)
   - Which part of the source supports this claim
   - Your confidence (high/medium/low)
   ```

3. **Cross-check externally**
   - Don't verify claims by asking the same model
   - Use search, primary sources, or domain experts
   - Click every link, verify every citation

4. **Ask for uncertainty explicitly**
   ```text
   What are you uncertain about in this response?
   What might be wrong?
   What would I need to verify?
   ```

5. **Use context-only mode**
   ```text
   Answer using ONLY the context I provided.
   If the answer isn't in the context, say "Not in provided context."
   Do not use information from your training data.
   ```

## Prevention

- Provide ground truth in context (don't make the model guess)
- Ask for uncertainty and caveats explicitly
- Use TL2+ verification for anything that will be shared
- Be skeptical of specificity (precise numbers, full citations)
- Click every link, verify every claim

## Quick prompts

### To detect
```text
List every factual claim in your response.
For each:
- Confidence: high/medium/low
- Source: context, training data, or uncertain
- What would make this wrong?
```

### To force uncertainty
```text
Before answering, state:
1. What you're confident about
2. What you're uncertain about
3. What you don't know

Then answer, flagging uncertain parts.
```

### To escape (context-only mode)
```text
Use ONLY the information below.
If something isn't explicitly stated, say "not in context."
Do not fill gaps with assumptions.

Context:
"""
[your context here]
"""

Question: [your question]
```

---

## Sources

Research on hallucination detection and mitigation:

- [S0001: Survey of Hallucination in NLG](../90_sources/extraction_cards/S0001_survey_hallucination_nlg.md) — hallucination taxonomy, types, mitigation
- [S0002: SelfCheckGPT](../90_sources/extraction_cards/S0002_selfcheckgpt.md) — self-consistency checking for hallucination
- [S0003: TruthfulQA](../90_sources/extraction_cards/S0003_truthfulqa.md) — truthfulness benchmarks
- [S0006: LMs Mostly Know What They Know](../90_sources/extraction_cards/S0006_lm_mostly_know_what_they_know.md) — calibration and uncertainty

---

## Related

- [Trust Calibration](../concepts/trust_calibration.md) — match verification to stakes
- [Verification Checklist](../reference/checklists/verification.md) — full verification process
- [Pushback Prompts](../reference/prompts/pushback.md) — demand evidence
- [Evidence Table Template](../reference/templates/evidence_table.md) — track claims and sources
