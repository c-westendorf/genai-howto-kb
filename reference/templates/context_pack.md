---
title: Context Pack Template
updated: 2026-01-17
---

# Context Pack Template

A universal template for structuring genAI input. Fill in the sections relevant to your task.

---

## Full template

```text
## Role
You are a [specific role with relevant expertise].

## Task
[Verb] [specific outcome] for [audience/purpose].

## Inputs
"""
[Paste the information the model should work with]
"""

## Constraints
- Length: [word/page limit]
- Tone: [formal/casual/technical/conversational]
- Audience: [who will use this]
- Avoid: [what NOT to include]
- Must include: [required elements]

## Format
[Specify structure: bullets, numbered list, table, JSON, narrative, etc.]

Example:
```
[Show what good output looks like]
```

## Quality bar
- [Criterion 1: e.g., "Each claim must be supported by the input"]
- [Criterion 2: e.g., "Actionable within 30 minutes"]
- [Criterion 3: e.g., "No jargon without definition"]
```

---

## Minimal template

For quick, low-stakes tasks:

```text
Role: [who]
Task: [what]
Constraints: [boundaries]
Format: [structure]
```

---

## Fill-in examples

### For analysis

```text
## Role
You are a senior data analyst.

## Task
Analyze this data to identify the top 3 factors driving churn.

## Inputs
"""
[Paste data or data summary]
"""

## Constraints
- Focus on actionable factors (things we can change)
- Quantify impact where possible
- Flag assumptions

## Format
1. Summary (3 sentences)
2. Top 3 factors with evidence
3. Recommended next steps
4. Assumptions and limitations

## Quality bar
- Claims tied to data
- Actionable recommendations
- Honest about uncertainty
```

### For writing

```text
## Role
You are a technical writer for developer documentation.

## Task
Write a how-to guide for setting up authentication.

## Inputs
"""
[Paste API docs, code samples, etc.]
"""

## Constraints
- Length: 500-800 words
- Audience: Developers new to this API
- Avoid: Assumed prior knowledge of our system
- Must include: Code examples, common errors

## Format
1. Overview (what and why)
2. Prerequisites
3. Step-by-step instructions with code
4. Common issues and solutions
5. Next steps

## Quality bar
- A developer can follow this without asking questions
- Code examples are copy-paste ready
- All steps are numbered
```

### For decisions

```text
## Role
You are a product strategist.

## Task
Recommend whether we should build Feature X or Feature Y.

## Inputs
"""
[Paste requirements, constraints, user feedback, etc.]
"""

## Constraints
- Consider: user impact, engineering effort, strategic fit
- Timeline: Q2 delivery
- Team: 2 engineers for 6 weeks

## Format
| Criterion | Feature X | Feature Y |
|-----------|-----------|-----------|
| [criterion] | [score] | [score] |

Recommendation: [choice]
Rationale: [why]

## Quality bar
- Trade-offs are explicit
- Recommendation is tied to criteria
- Risks are identified
```

---

## Checklist before prompting

- [ ] **Role** is specific (not "helpful assistant")
- [ ] **Task** is clear verb + outcome
- [ ] **Inputs** contain what's needed (not more, not less)
- [ ] **Constraints** are explicit (not assumed)
- [ ] **Format** is specified (not left to model's choice)
- [ ] **Quality bar** is defined (you'll know if it's good)

---

## Common mistakes

| Mistake | Problem | Fix |
|---------|---------|-----|
| Generic role | Model uses default behavior | Be specific: "senior data scientist specializing in experimentation" |
| Vague task | Model guesses what you want | Use clear verb: "Compare," "Summarize," "Generate" |
| No constraints | Model makes assumptions | State length, tone, audience, what to avoid |
| No format | Model picks one randomly | Show example of good output |
| No quality bar | Can't tell if output is good | Define what "done" looks like |

---

## Related

- [Context Engineering](../../concepts/context_engineering.md) — the underlying concept
- [Context pack checklist](../checklists/context_pack.md) — validation checklist
- [Context Bloat](../../pitfalls/context_bloat.md) — when context is too much
