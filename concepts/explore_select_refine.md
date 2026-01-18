---
title: Explore → Select → Refine
updated: 2026-01-17
refs: [S0017, S0007, S0008]
---

# Explore → Select → Refine

## What it is

The thought partnership loop. Instead of accepting the first answer, you:

1. **Explore** — diverge, generate options, surface assumptions
2. **Select** — converge, choose with criteria, commit to an approach
3. **Refine** — iterate, critique, improve to quality bar

This is how you treat genAI as a collaborator, not a vending machine.

## Why it matters

**If you skip this:**
- You're stuck with the first answer (often not the best)
- You miss alternative approaches that might be better
- You don't discover hidden assumptions until too late
- You iterate on symptoms instead of finding the right frame

**If you do this:**
- You see the option space before committing
- You make explicit decisions with criteria
- You catch wrong assumptions early
- Your final output is deliberate, not accidental

## How to apply it

### Phase 1: Explore (diverge)

**Goal**: Generate meaningfully different options and surface what you don't know.

**What to ask for:**
- Multiple approaches (3-5 minimum)
- Clarifying questions about gaps
- Hidden assumptions and risks
- When each approach would fail

**Prompt template:**
```text
You are my thought partner.

Task: [what I'm trying to accomplish]
Context: [relevant background]
Constraints: [time, tone, audience, format]

Before solving, please:
1. Ask 5-10 clarifying questions (grouped by: goal, constraints, domain).
2. Propose 3-5 meaningfully different approaches.
3. For each approach: strengths, weaknesses, and when it fails.
4. Recommend which to try first and why.
```

**Stop when:**
- You have 3-5 meaningfully different approaches
- The clarifying questions reveal real gaps you need to fill
- You understand the trade-offs between options

### Phase 2: Select (converge)

**Goal**: Choose one approach based on explicit criteria.

**What to ask for:**
- A decision tied to your priorities
- Success criteria (how you'll know it worked)
- Next steps (concrete, actionable)
- Risks and mitigations

**Prompt template:**
```text
Here are the approaches we explored: [paste or summarize]

My priorities (ranked):
1. [e.g., speed]
2. [e.g., correctness]
3. [e.g., low risk]

Pick one approach. Return:
- Decision: which approach
- Rationale: why, tied to my priorities
- Success criteria: how we'll know it worked
- Next steps: concrete actions
- Risks: what could go wrong and how to mitigate
```

**Stop when:**
- One approach clearly wins on your criteria
- You have measurable success criteria
- You know the first concrete step

### Phase 3: Refine (iterate)

**Goal**: Improve output until it meets quality bar.

**What to ask for:**
- Critique against specific criteria
- Rewrite to higher standard
- Final checklist before shipping

**Prompt template:**
```text
Here is the current draft: [paste]

Please:
1. Critique it against: clarity, correctness, completeness, usefulness.
2. Identify the weakest part.
3. Rewrite to a higher standard.
4. Add a checklist I can use before shipping.
```

**The micro-loop** (repeat as needed):
1. **Draft** — generate
2. **Critique** — stress-test
3. **Edit** — improve
4. **Verify** — check claims

**Stop when:**
- Output meets your quality bar
- Checklist passes
- Further iteration yields diminishing returns

## Signs you're doing it well

- You see options you wouldn't have thought of
- Your final choice is deliberate, not default
- Refinement feels like polishing, not rescuing
- You can explain why you chose this approach over others

## Signs you're doing it wrong

- All options look the same → Push for more divergent approaches
- You skip select and jump to refining the first option → Go back and compare
- Refine phase takes forever → Your explore/select phases missed something
- You keep starting over → See [Getting Stuck](../pitfalls/getting_stuck.md)

## Quick reference

### Explore prompt
```text
Give me 5 meaningfully different approaches to [task].
For each: describe the approach, strengths, weaknesses, and when it would fail.
```

### Select prompt
```text
Compare these approaches against my priorities: [list priorities].
Pick one. Explain why. Give me success criteria and next steps.
```

### Refine prompt
```text
Critique this against [criteria]. What's the weakest part?
Rewrite to a higher standard. Add a pre-ship checklist.
```

### Stop conditions summary

| Phase | Continue if... | Stop when... |
|-------|----------------|--------------|
| Explore | Options too similar, gaps unclear | 3-5 different approaches, trade-offs clear |
| Select | Criteria not met, tie between options | One approach wins, next steps clear |
| Refine | Below quality bar, weak spots remain | Quality bar met, checklist passes |

---

## Sources

Concepts in this guide are grounded in research and best practices:

- [S0017: The Centaur Programmer](../90_sources/extraction_cards/S0017_centaur_programmer.md) — human+AI workflow patterns
- [S0018: Mollick Prompting AI Learner Guide](../90_sources/extraction_cards/S0018_mollick_prompting_learner_guide.md) — iterative prompting, not accepting first answer
- [S0007: OpenAI Prompt Engineering Best Practices](../90_sources/extraction_cards/S0007_openai_prompt_engineering_best_practices.md) — iteration as core practice

---

## Related

- [Context Engineering](context_engineering.md) — packaging context for each phase
- [Trust Calibration](trust_calibration.md) — verification in the refine phase
- [Getting Stuck](../pitfalls/getting_stuck.md) — when the loop breaks down
- [Explore Prompts](../reference/prompts/explore.md) — copy-paste prompts for explore phase
