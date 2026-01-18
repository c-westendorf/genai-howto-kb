---
title: Options Table Template
updated: 2026-01-17
---

> **Navigation**: [START HERE](../../START_HERE.md) · [Concepts](../../concepts/index.md) · [Pitfalls](../../pitfalls/index.md) · [Decisions](../../decisions/index.md) · [Playbooks](../../playbooks/index.md) · [Reference](../index.md)
>
> **In this section**: [Context Pack](context_pack.md) · [Options Table](options_table.md) · [Evidence Table](evidence_table.md) · [GSD Task Spec](gsd_task_spec.md) · [RALPH State Files](ralph_state_files.md)

# Options Table Template

Template for comparing options during the Select phase. Use to structure decisions.

---

## Basic options table

Copy and fill in:

```markdown
## Decision: [What we're deciding]

### Context
[1-2 sentences on why this decision is needed now]

### Options

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| A: [Name] | [Brief description] | [Key advantages] | [Key disadvantages] |
| B: [Name] | [Brief description] | [Key advantages] | [Key disadvantages] |
| C: [Name] | [Brief description] | [Key advantages] | [Key disadvantages] |

### Recommendation
[Which option and why]
```

---

## Weighted criteria table

For decisions with multiple evaluation criteria:

```markdown
## Decision: [What we're deciding]

### Evaluation criteria
1. [Criterion 1] — [why it matters]
2. [Criterion 2] — [why it matters]
3. [Criterion 3] — [why it matters]

### Options comparison

| Criterion | Weight | Option A | Option B | Option C |
|-----------|--------|----------|----------|----------|
| [Criterion 1] | [H/M/L] | [Score: 1-5] | [Score: 1-5] | [Score: 1-5] |
| [Criterion 2] | [H/M/L] | [Score: 1-5] | [Score: 1-5] | [Score: 1-5] |
| [Criterion 3] | [H/M/L] | [Score: 1-5] | [Score: 1-5] | [Score: 1-5] |
| **Weighted total** | — | [Total] | [Total] | [Total] |

### Notes
- Option A: [Key consideration]
- Option B: [Key consideration]
- Option C: [Key consideration]

### Recommendation
[Which option, tied to criteria scoring]
```

---

## Risk-focused options table

For decisions where risk is primary concern:

```markdown
## Decision: [What we're deciding]

### Options with risk analysis

| Option | Approach | Best case | Worst case | Likelihood of success | Reversibility |
|--------|----------|-----------|------------|----------------------|---------------|
| A: [Name] | [How it works] | [If it works] | [If it fails] | [H/M/L] | [Easy/Hard] |
| B: [Name] | [How it works] | [If it works] | [If it fails] | [H/M/L] | [Easy/Hard] |
| C: [Name] | [How it works] | [If it works] | [If it fails] | [H/M/L] | [Easy/Hard] |

### Risk tolerance
[What level of risk is acceptable for this decision?]

### Recommendation
[Which option, based on risk profile]
```

---

## Trade-off matrix

For decisions with inherent trade-offs:

```markdown
## Decision: [What we're deciding]

### Trade-off dimensions
- [Dimension 1] vs. [Dimension 1 opposite] (e.g., speed vs. quality)
- [Dimension 2] vs. [Dimension 2 opposite] (e.g., cost vs. capability)

### Options positioned on trade-offs

| Option | [Dimension 1] | [Dimension 2] | Sweet spot for... |
|--------|---------------|---------------|-------------------|
| A: [Name] | [Where it falls] | [Where it falls] | [When to choose] |
| B: [Name] | [Where it falls] | [Where it falls] | [When to choose] |
| C: [Name] | [Where it falls] | [Where it falls] | [When to choose] |

### Our priority
[Which dimension matters most and why]

### Recommendation
[Which option, based on priority]
```

---

## Build vs. buy table

For make/buy decisions:

```markdown
## Decision: [What capability we need]

### Build option

| Factor | Assessment |
|--------|------------|
| Development time | [Estimate] |
| Development cost | [Estimate] |
| Ongoing maintenance | [Estimate] |
| Control/customization | [High/Medium/Low] |
| Risk | [Key risks] |

### Buy option(s)

| Factor | Vendor A | Vendor B |
|--------|----------|----------|
| Cost (upfront) | [Amount] | [Amount] |
| Cost (ongoing) | [Amount/period] | [Amount/period] |
| Time to implement | [Estimate] | [Estimate] |
| Fit with requirements | [%] | [%] |
| Vendor risk | [Assessment] | [Assessment] |

### Decision criteria
1. [What matters most]
2. [What matters second]
3. [What we're willing to trade off]

### Recommendation
[Build or buy, and why]
```

---

## Technology selection table

For choosing between technical approaches:

```markdown
## Decision: [Technology/approach needed for]

### Requirements
- Must have: [List]
- Should have: [List]
- Nice to have: [List]

### Options

| Factor | Option A | Option B | Option C |
|--------|----------|----------|----------|
| **Must have** | | | |
| [Requirement 1] | ✓/✗ | ✓/✗ | ✓/✗ |
| [Requirement 2] | ✓/✗ | ✓/✗ | ✓/✗ |
| **Should have** | | | |
| [Requirement 3] | ✓/✗ | ✓/✗ | ✓/✗ |
| [Requirement 4] | ✓/✗ | ✓/✗ | ✓/✗ |
| **Nice to have** | | | |
| [Requirement 5] | ✓/✗ | ✓/✗ | ✓/✗ |
| **Other factors** | | | |
| Team familiarity | [H/M/L] | [H/M/L] | [H/M/L] |
| Community/support | [H/M/L] | [H/M/L] | [H/M/L] |
| Long-term viability | [H/M/L] | [H/M/L] | [H/M/L] |

### Recommendation
[Which option, with rationale]
```

---

## Prompts to generate options tables

### Generate options

```text
I need to decide: [decision]

Context:
- [Relevant context]
- [Constraints]

Generate 3-4 options as a comparison table:
- Include pros and cons for each
- Make options genuinely different (not strawmen)
- Identify the key trade-offs

End with: "What criteria should we use to choose?"
```

### Evaluate against criteria

```text
Here are my options:
[paste options]

Evaluate against these criteria:
1. [Criterion 1]
2. [Criterion 2]
3. [Criterion 3]

Create a weighted comparison table.
Rate each option 1-5 on each criterion.
Show your reasoning for each rating.
```

### Stress-test the recommendation

```text
I'm leaning toward [option].

Challenge this choice:
1. What could go wrong?
2. When would another option be better?
3. What am I not seeing?
4. What would make me regret this choice in 6 months?
```

---

## Related

- [Analysis Playbook](../../playbooks/analysis.md) — decision analysis patterns
- [Select Prompts](../prompts/select.md) — prompts for the select phase
- [Evidence Table Template](evidence_table.md) — for grounding claims
