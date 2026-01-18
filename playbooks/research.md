---
title: Research & Synthesis Playbook
updated: 2026-01-17
refs: [S0004, S0023]
---

# Research & Synthesis Playbook

## When to use this

- Finding and synthesizing information on a topic
- Building understanding before making decisions
- Creating literature reviews or background docs
- Answering "what do we know about X?"

---

## Context template

```text
Role: You are a research analyst specializing in [domain].

Task: Research [topic] to answer [core question].

Constraints:
- Depth: [overview / deep dive / comprehensive]
- Time: [how much time for research]
- Sources: [what types of sources are acceptable]
- Output: [summary / synthesis / annotated bibliography]

Quality bar:
- Claims are sourced
- Uncertainties are flagged
- Gaps in knowledge are identified
```

---

## Prompt sequence

### 1. Explore: Define research questions

```text
I need to research: [topic]

Core question: [what I'm trying to answer]

Help me:
1. Break this into 5-10 specific research questions
2. Rank by importance
3. Identify what "good evidence" looks like for each
4. Flag questions that are hard to answer definitively
```

### 2. Select: Build search strategy

```text
For these research questions: [list]

Create a search plan:
1. Keywords and search terms
2. Types of sources to prioritize (academic, industry, official docs)
3. Domains/publications known to be authoritative
4. What would disconfirm current assumptions
```

### 3. Refine: Extract and synthesize

**For each source:**
```text
Extract from this source:

Source: [title, author, date, URL]

1. Key claims (with page/section references)
2. Evidence quality (strong/moderate/weak)
3. Limitations or caveats
4. How it answers our research questions
5. Conflicts with other sources (if any)
```

**Synthesis:**
```text
Given these extractions: [paste]

Create a synthesis:
1. Executive summary (1 paragraph)
2. Key findings by research question
3. Areas of consensus
4. Areas of disagreement or uncertainty
5. Gaps in the research
6. Recommended next steps
```

---

## Verification checklist

Before using research:

- [ ] **Sources verified**: Links work, sources exist
- [ ] **Claims traced**: Each claim maps to a source
- [ ] **Recency checked**: Information is current enough
- [ ] **Bias considered**: Source perspectives acknowledged
- [ ] **Gaps identified**: Know what you don't know
- [ ] **Confidence calibrated**: Strong vs. weak evidence distinguished

---

## Common pitfalls

| Pitfall | Signs | Fix |
|---------|-------|-----|
| [Hallucinated citations](../pitfalls/hallucinations.md) | Sources don't exist | Click every link, verify every source |
| Confirmation bias | Only found supporting evidence | Explicitly search for disconfirming evidence |
| Outdated information | Using old sources for fast-moving topics | Check publication dates, search for updates |
| Over-reliance on model knowledge | Model answered without sources | Use context-only mode, demand citations |
| Shallow synthesis | Summary but no insight | Ask "so what?" and "what does this mean for us?" |

---

## Patterns

### Pattern: Question decomposition

Start vague, get specific:

```text
Topic: [broad topic]

Turn this into research questions:
1. What do I need to know? (5-10 questions)
2. Which are most important for my goal?
3. Which are answerable vs. need original research?
4. What would change my thinking if I learned it?
```

### Pattern: Source triage

Evaluate sources before using:

```text
For this source: [title, URL]

Evaluate:
1. Authority: Who wrote this? What's their expertise?
2. Recency: When was this published? Still relevant?
3. Evidence: Claims supported or just assertions?
4. Bias: What perspective might color this?
5. Verdict: Use / Use with caution / Skip
```

### Pattern: Context-only research

Force grounding in provided sources:

```text
Use ONLY the sources I provide below.
If something isn't in these sources, say "not covered in provided sources."
Do not use information from your training data.

Sources:
"""
[paste source content]
"""

Question: [your question]
```

### Pattern: Synthesis with uncertainty

For honest synthesis:

```text
Synthesize these findings: [paste]

For each conclusion:
- Confidence: high/medium/low
- Evidence strength: strong/moderate/weak
- Sources that agree
- Sources that disagree or qualify
- What would change this conclusion
```

### Pattern: Gap analysis

Know what you don't know:

```text
Based on this research: [summary]

What are we missing?
1. Questions we can't answer with current sources
2. Perspectives not represented
3. Recent developments that might change things
4. Where experts would disagree with our conclusions
```

---

## Source quality hierarchy

Use this to prioritize sources:

| Tier | Source type | When to use |
|------|-------------|-------------|
| 1 | Peer-reviewed papers, official standards | High-stakes claims |
| 2 | Government/regulatory docs, major org reports | Policy, compliance |
| 3 | Official vendor documentation | Product-specific info |
| 4 | Industry analysis, reputable journalism | Context, trends |
| 5 | Blog posts, opinions, forums | Leads only, verify elsewhere |

---

## Related

- [Trust Calibration](../concepts/trust_calibration.md) — verification intensity
- [Hallucinations](../pitfalls/hallucinations.md) — citation risks
- [Pushback prompts](../reference/prompts/pushback.md) — demanding evidence
- [Verification checklist](../reference/checklists/verification.md) — verification process
