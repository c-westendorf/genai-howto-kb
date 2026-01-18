---
title: Writing & Drafting Playbook
updated: 2026-01-17
refs: [S0007, S0008]
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Writing](writing.md) · [Analysis](analysis.md) · [Research](research.md) · [Code](code.md) · [Meetings](meetings.md) · [DS Patterns](ds_patterns.md) · [MLE Patterns](mle_patterns.md) · [GSD+RALPH](mle_gsd_ralph.md) · [Business](business_patterns.md)

# Writing & Drafting Playbook

## When to use this

- PRDs, docs, emails, reports, summaries
- Any task where the output is written text
- When you need to produce a polished artifact

---

## Context template

```text
Role: You are a [writer type: technical writer / communications lead / analyst].

Task: Write [artifact type] about [topic] for [audience].

Inputs:
"""
[Paste source material, key points, or requirements]
"""

Constraints:
- Length: [word count / page count]
- Tone: [formal / casual / technical / persuasive]
- Audience: [who reads this, what they know]
- Must include: [required elements]
- Avoid: [what not to include]

Format: [structure: sections, bullets, narrative]

Quality bar:
- [Reader can understand without questions]
- [Actionable / informative / persuasive — pick one]
- [Specific, not generic]
```

---

## Prompt sequence

### 1. Explore: Generate structure options

```text
I need to write [artifact] about [topic] for [audience].

Give me 3 different structural approaches:
- Approach A: [e.g., problem-solution-action]
- Approach B: [e.g., chronological narrative]
- Approach C: [e.g., bottom-line-up-front]

For each: outline, strengths, weaknesses, best for what audience.
```

### 2. Select: Choose and outline

```text
I'll use approach [X].

Create a detailed outline:
- Main sections with headers
- Key points for each section
- Where evidence/examples go
- Estimated word count per section
```

### 3. Refine: Draft and iterate

**First draft:**
```text
Using this outline, write section [1].

Constraints:
- [length]
- [tone]
- [specific requirements]
```

**Critique:**
```text
Critique this draft against:
- Clarity: can the audience understand it?
- Completeness: any gaps?
- Tone: does it match [target tone]?
- Actionability: can they do something with this?

Identify the top 3 issues.
```

**Rewrite:**
```text
Rewrite to address:
1. [issue 1]
2. [issue 2]
3. [issue 3]

Keep what's working. Fix what's not.
```

---

## Verification checklist

Before shipping:

- [ ] **Clear**: Audience can understand without asking questions
- [ ] **Complete**: All required elements included
- [ ] **Correct**: Facts verified (at appropriate trust level)
- [ ] **Consistent**: Tone and style consistent throughout
- [ ] **Actionable**: Reader knows what to do next (if applicable)
- [ ] **Concise**: No unnecessary words or sections

---

## Common pitfalls

| Pitfall | Signs | Fix |
|---------|-------|-----|
| [Generic outputs](../pitfalls/generic_outputs.md) | Sounds like any company | Add specific examples, ban hedging |
| Too long | Exceeds length, readers skim | Cut ruthlessly, move details to appendix |
| Wrong tone | Doesn't match audience | Specify persona, provide examples |
| Missing structure | Wall of text | Start with outline, use headers |
| Unsupported claims | Facts without sources | Use fact-safe pattern below |

---

## Patterns

### Pattern: Outline → Draft → Critique → Rewrite

For any substantial document:

```text
Step 1: Create outline for [topic] for [audience].
Step 2: Draft section by section.
Step 3: Critique each section for clarity and gaps.
Step 4: Rewrite based on critique.
Step 5: Final read for consistency.
```

### Pattern: Style transfer

Match an existing style:

```text
Rewrite this to match the following style:
- Tone: [direct / warm / technical]
- Sentence length: [short / varied / long]
- Voice: [active / passive]
- Vocabulary: [simple / technical / jargon-free]
- Banned phrases: [list any to avoid]

Text to rewrite:
"""
[paste text]
"""
```

### Pattern: Fact-safe writing

For medium/high stakes:

```text
Write this with strict rules:
1. Any factual claim must be supported by provided context or cited source
2. If you can't cite, mark as "[needs verification]"
3. Opinions and inferences must be labeled as such
4. No invented specifics (numbers, names, dates)
```

### Pattern: BLUF (Bottom Line Up Front)

For busy readers:

```text
Structure:
1. Bottom line (1-2 sentences): the key takeaway
2. Supporting points (3-5 bullets): why this is true
3. Details: for those who want more
4. Next steps: what to do

Write [topic] in this structure for [audience].
```

---

## Related

- [Context Engineering](../concepts/context_engineering.md) — structuring your input
- [Refine prompts](../reference/prompts/refine.md) — iteration prompts
- [Generic Outputs](../pitfalls/generic_outputs.md) — when writing is too bland
