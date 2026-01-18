---
title: Evidence Table Template
updated: 2026-01-17
---

# Evidence Table Template

Template for tracking claims and evidence. Use to verify outputs and ground decisions.

---

## Basic evidence table

Copy and fill in:

```markdown
## Topic: [What this evidence supports]

| Claim | Evidence | Source | Confidence | Verified? |
|-------|----------|--------|------------|-----------|
| [Claim 1] | [Supporting evidence] | [Where from] | H/M/L | ☐ |
| [Claim 2] | [Supporting evidence] | [Where from] | H/M/L | ☐ |
| [Claim 3] | [Supporting evidence] | [Where from] | H/M/L | ☐ |

### Notes
- [Any caveats or context]
```

---

## Detailed evidence table

For rigorous verification:

```markdown
## Topic: [What this evidence supports]

| # | Claim | Evidence | Source | Source type | Date | Confidence | Verified by | Notes |
|---|-------|----------|--------|-------------|------|------------|-------------|-------|
| 1 | [Claim] | [Evidence] | [Source] | [Type] | [Date] | H/M/L | [Name/—] | [Notes] |
| 2 | [Claim] | [Evidence] | [Source] | [Type] | [Date] | H/M/L | [Name/—] | [Notes] |

### Source types
- **Primary**: Original research, official documentation, firsthand data
- **Secondary**: Analysis of primary sources, reputable journalism
- **Tertiary**: Aggregated info, encyclopedias, general references
- **Model knowledge**: From LLM training, no external source

### Confidence levels
- **High**: Multiple reliable sources, directly verifiable
- **Medium**: Single reliable source, or inference from strong evidence
- **Low**: Weak source, old data, or significant uncertainty

### Verification status
- ✓ Verified: Checked against source, confirmed accurate
- ☐ Unverified: Not yet checked
- ✗ Failed: Checked, found inaccurate or unsupported
```

---

## Claims audit table

For auditing AI outputs:

```markdown
## Audit: [What AI output is being audited]

| Claim made | Claim type | Source provided? | Source verified? | Accuracy | Action |
|------------|------------|------------------|------------------|----------|--------|
| [Claim] | Fact/Inference/Opinion | Y/N | Y/N/NA | ✓/✗/? | [Action] |

### Claim types
- **Fact**: Verifiable statement about reality
- **Inference**: Conclusion drawn from facts
- **Opinion**: Subjective judgment or recommendation
- **Speculation**: Uncertain claim about unknowns

### Actions
- Accept: Claim verified, use as-is
- Verify: Need to check before using
- Flag: Mark as uncertain in output
- Remove: Claim unsupported, delete
- Correct: Claim wrong, fix
```

---

## Source credibility table

For evaluating source quality:

```markdown
## Source evaluation: [Topic]

| Source | Type | Authority | Recency | Bias risk | Reliability |
|--------|------|-----------|---------|-----------|-------------|
| [Source 1] | [Type] | [H/M/L] | [Current/Dated] | [H/M/L] | [H/M/L] |
| [Source 2] | [Type] | [H/M/L] | [Current/Dated] | [H/M/L] | [H/M/L] |

### Evaluation criteria

**Authority**
- High: Recognized expert, official source, peer-reviewed
- Medium: Reputable organization, experienced practitioner
- Low: Unknown author, user-generated, unvetted

**Recency**
- Current: Within relevant timeframe for topic
- Dated: May be outdated, verify currency

**Bias risk**
- High: Financial interest, advocacy organization, known bias
- Medium: Some potential bias, generally balanced
- Low: Neutral party, multiple perspectives represented

**Reliability**
- High: Consistently accurate, fact-checked, primary source
- Medium: Generally reliable, some errors possible
- Low: Unreliable history, aggregated without verification
```

---

## Research evidence matrix

For synthesizing multiple sources:

```markdown
## Research question: [What we're trying to answer]

### Evidence matrix

| Finding | Source 1 | Source 2 | Source 3 | Consensus |
|---------|----------|----------|----------|-----------|
| [Finding 1] | ✓/✗/— | ✓/✗/— | ✓/✗/— | [Strong/Weak/Mixed] |
| [Finding 2] | ✓/✗/— | ✓/✗/— | ✓/✗/— | [Strong/Weak/Mixed] |
| [Finding 3] | ✓/✗/— | ✓/✗/— | ✓/✗/— | [Strong/Weak/Mixed] |

### Legend
- ✓ Supports this finding
- ✗ Contradicts this finding
- — Does not address

### Synthesis
[What the evidence tells us overall]

### Gaps
[What we don't have evidence for]
```

---

## Decision evidence table

For grounding a decision in evidence:

```markdown
## Decision: [What we decided]

### Evidence supporting this decision

| Factor | Evidence | Weight | Source |
|--------|----------|--------|--------|
| [Factor 1] | [What we know] | [H/M/L] | [Source] |
| [Factor 2] | [What we know] | [H/M/L] | [Source] |

### Evidence against (considered)

| Concern | Evidence | Why we proceeded anyway |
|---------|----------|-------------------------|
| [Concern 1] | [Evidence] | [Reasoning] |
| [Concern 2] | [Evidence] | [Reasoning] |

### Assumptions (not evidence-based)

| Assumption | Risk if wrong | How we'd know |
|------------|---------------|---------------|
| [Assumption 1] | [Impact] | [Signal] |
| [Assumption 2] | [Impact] | [Signal] |
```

---

## Prompts to generate evidence tables

### Extract claims for verification

```text
From this content:
"""
[paste content]
"""

Extract all factual claims into a table:
| Claim | Evidence provided | Source cited | Confidence | Needs verification? |

Focus on claims that:
1. State facts about the world
2. Cite statistics or data
3. Reference specific sources
4. Make predictions or causal claims
```

### Audit AI output

```text
Audit this AI-generated content:
"""
[paste content]
"""

Create an evidence table:
1. List each factual claim
2. Note if evidence was provided
3. Identify claims that should be verified
4. Flag anything that might be fabricated

Be skeptical — assume claims need verification unless obviously true.
```

### Build source credibility assessment

```text
I'm using these sources for [topic]:
1. [Source 1]
2. [Source 2]
3. [Source 3]

Evaluate each source:
- Authority: How expert/official is this source?
- Recency: Is the information current?
- Bias: What biases might affect this source?
- Reliability: How trustworthy historically?

Create a source credibility table.
```

### Synthesize across sources

```text
I have these findings from multiple sources:

Source 1: [findings]
Source 2: [findings]
Source 3: [findings]

Create an evidence matrix:
1. What do sources agree on?
2. What do they disagree on?
3. What's the overall weight of evidence?
4. What gaps remain?
```

---

## Related

- [Verification Checklist](../checklists/verification.md) — verification process
- [Trust Calibration](../../concepts/trust_calibration.md) — matching verification to stakes
- [Hallucinations](../../pitfalls/hallucinations.md) — detecting fabricated content
- [Research Playbook](../../playbooks/research.md) — research patterns
