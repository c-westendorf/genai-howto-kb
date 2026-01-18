---
title: Explore → Select → Refine
updated: 2026-01-18
refs: [S0017, S0007, S0008]
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Context Engineering](context_engineering.md) · [Explore → Select → Refine](explore_select_refine.md) · [Trust Calibration](trust_calibration.md) · [Parallel Execution](parallel_execution.md) · [Decision Flow](decision_flow.md) · [One-Shot Planning](oneshot_planning.md)

# Explore → Select → Refine

## What it is

The thought partnership loop. Instead of accepting the first answer, you:

1. **Explore** — diverge, generate options, surface assumptions
2. **Select** — converge, choose with criteria, commit to an approach
3. **Refine** — iterate, critique, improve to quality bar

This is how you treat genAI as a collaborator, not a vending machine.

## Quickstart

**Use ESR when:**
- You need to turn a vague topic into a clear question, plan, or decision
- You want genAI as a thought partner (options → decision → quality bar)
- You're unsure what the right next move is

**Before you start, gather:**
- Topic/task: what you're trying to accomplish
- Audience/decision owner: who this is for
- Constraints: must-haves, must-avoids
- Stakes: low / medium / high

**Expected outputs:**
- 3-5 distinct directions (Explore)
- 1 selected direction + decision criteria (Select)
- Refined spec + verification checklist + next action (Refine)

**Runnable prompt:**
```text
You are my thought partner. We will run Explore → Select → Refine.

Context:
- Topic/task: <what you're trying to accomplish>
- Audience/decision owner: <who this is for>
- Constraints: <must-haves, must-avoids>
- Stakes: <low/medium/high>

1) EXPLORE: Generate 3-5 meaningfully different directions.
   For each: what it is, assumptions, risks/unknowns.
   Ask clarifying questions if constraints are missing.

2) SELECT: Ask me for decision criteria if not provided.
   Compare directions against criteria.
   Recommend one and explain why it wins.

3) REFINE: Convert the selected direction into a refined spec.
   Include: success criteria, non-goals, verification checklist, first next action.
   Then critique it and iterate once.
```

---

## Thought partnership model: GTD + ESR

ESR is the **reasoning engine**. GTD is the **control system** that makes reasoning repeatable across sessions.

**Integrated loop:**
1. **Capture** — dump inputs, unknowns, constraints (working set)
2. **Explore** — generate options + surface assumptions *(ESR)*
3. **Select** — decide with criteria + success measures *(ESR)*
4. **Organize** — persist artifacts so next session is deterministic
5. **Refine** — critique/verify against quality bar *(ESR)*
6. **Engage** — execute the plan
7. **Reflect** — short review: what changed, what to update, what to stop

**Organize: what to persist**

| Item | Purpose | Examples |
|------|---------|----------|
| Working set | Reduce context thrash | Notes, constraints list |
| Decision criteria | Prevent re-litigation | Criteria + tradeoffs |
| Spec/plan/guardrails | Deterministic next run | Spec + plan + rules |
| Verification checklist | Quality gate | Evidence + tests |
| Reflect notes | Improve process | Short retro bullets |

---

## Ownership mapping

| Step | Human owns | GenAI owns | Joint output |
|------|------------|------------|--------------|
| Capture | Intent, stakes, constraints | Extraction, clustering | Working set |
| Explore | What "distinct" means | Options, assumptions | Option set |
| Select | Decision + risk acceptance | Tradeoff analysis | Chosen path + criteria |
| Organize | What is authoritative | Structuring + formatting | Persisted artifacts |
| Refine | Acceptance bar | Critique + tightening | Refined output + checks |
| Engage | Final accountability | Execution assistance | Shipped work |
| Reflect | Learning + priorities | Pattern spotting | Updated playbook |

> **Rule:** If decision criteria are missing, Select must pause and ask for them.

---

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

**Goal:** Generate meaningfully different options and surface what you don't know.

**Inputs:** Topic/task, constraints, stakes level

**Output:** 3-5 distinct directions with assumptions, risks, and trade-offs

**Prompt:**
```text
Generate 3-5 meaningfully different approaches to [task].
For each: what it is, key assumptions, risks/unknowns, when it would fail.
Ask 1-3 clarifying questions if constraints are missing.
```

**Stop when:**
- You have 3-5 genuinely different approaches (not minor variants)
- Trade-offs between options are clear
- You understand what you'd give up with each choice

**Failure modes:**
- Options all sound the same → [Generic Outputs](../pitfalls/generic_outputs.md)
- Output gets worse as you add context → [Context Bloat](../pitfalls/context_bloat.md)
- Spinning without progress → [Getting Stuck](../pitfalls/getting_stuck.md)

### Phase 2: Select (converge)

**Goal:** Choose one approach based on explicit criteria.

**Inputs:** Explored options, your decision criteria / priorities

**Output:** Chosen direction + rationale + success criteria + what would change your mind

**Prompt:**
```text
Compare these approaches against my priorities: [list priorities].
Pick one. Explain:
- Why it wins
- What we give up
- Success criteria
- What would change your recommendation
```

**Stop when:**
- One approach clearly wins on your criteria
- You have measurable success criteria
- You know the first concrete step

**Failure modes:**
- Can't decide (tie) → Clarify criteria or add constraints
- Criteria missing → Pause and define them before proceeding
- Over/under-verifying for stakes → [Trust Miscalibration](../pitfalls/trust_miscalibration.md)

### Phase 3: Refine (iterate)

**Goal:** Improve output until it meets quality bar.

**Inputs:** Selected direction, acceptance criteria, draft output

**Output:** Refined spec/output + verification checklist + first next action

**Prompt:**
```text
Critique this against: clarity, correctness, completeness, usefulness.
What's the weakest part? Rewrite to a higher standard.
Add a verification checklist and first next action.
```

**The micro-loop** (repeat as needed):
1. **Draft** — generate
2. **Critique** — stress-test
3. **Edit** — improve
4. **Verify** — check claims (if factual claims are involved, apply evidence standards)

**Stop when:**
- Output meets your quality bar
- Verification checklist passes
- Further iteration yields diminishing returns

**Failure modes:**
- Refine phase takes forever → Explore/Select missed something; go back
- Confident but wrong claims → [Hallucinations](../pitfalls/hallucinations.md)
- Over/under-verifying for stakes → [Trust Miscalibration](../pitfalls/trust_miscalibration.md)

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

## Handoff: When ESR is done

**Move to Engage when you have:**
- A refined spec/output
- Success criteria + non-goals
- A verification checklist
- A first next action

**After execution, Reflect (2-5 min):**
- What changed from the plan?
- What should be updated (criteria, guardrails, templates)?
- What should stop happening?

---

## Full prompt library

For copy-paste prompts, see [Reference](../reference/index.md).

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

---

**Page contract:**
- This page explains ESR and provides minimal runnable prompts
- Full prompt library → [Reference](../reference/index.md)
- Recovery tactics → [Pitfalls](../pitfalls/index.md)
