---
title: The Decision Flow
updated: 2026-01-17
refs: [S0007, S0008, S0012, S0023]
---

# The Decision Flow

## What it is

A practical sequence for deciding *how* to work with genAI on a given task. Before you prompt, decide: What kind of task? What's at stake? What pattern fits? How much verification?

## Why it matters

**If you skip this:**
- You use the same approach for everything
- Low-stakes work is over-verified (slow)
- High-stakes work is under-verified (risky)
- You don't match the pattern to the task

**If you do this:**
- Approach matches the task type
- Verification matches the stakes
- You're deliberate about how you work
- Results are more consistent

## The flow

### Step 0: Classify the task

What's the dominant job type?

| Type | What it means | Examples |
|------|---------------|----------|
| **Transform** | Change form, keep meaning | Summarize, rewrite, extract, translate |
| **Generate** | Create options, ideas, drafts | Brainstorm, draft, ideate |
| **Reason/Decide** | Analyze, compare, recommend | Diagnose, compare trade-offs, plan |
| **Compute** | Calculate, code, analyze data | Math, logic, code, data analysis |
| **Research** | Find, synthesize, cite | Collect sources, synthesize, cite |
| **Act** | Execute, change systems | Tool use, sending, executing |

### Step 1: Determine stakes

Ask:
- **If this is wrong, what breaks?** (money, health, legal, reputation, security)
- **How reversible is the outcome?**
- **Who relies on this?**

| Stakes | Examples |
|--------|----------|
| **Low** | Internal drafts, brainstorming, exploration |
| **Medium** | Shared docs, team decisions, customer-facing |
| **High** | Legal, financial, security, medical, public |

### Step 2: Choose trust posture

Match trust to stakes:

| Posture | When | What it means |
|---------|------|---------------|
| **Draft mode** | Low stakes | Treat as starting point. Iterate fast. |
| **Verified mode** | Medium stakes | Require citations, check claims, human review. |
| **Assured mode** | High stakes | Authoritative sources, expert signoff, audit trail. |

### Step 3: Choose interaction pattern

| Pattern | When to use |
|---------|-------------|
| **Single-shot** | Simple, low-stakes, well-defined format |
| **Thought partnership** | Need to explore options, complex reasoning |
| **Parallel execution** | Need breadth, multiple perspectives, high complexity |

See [Which pattern?](../decisions/which_pattern.md) for decision tree.

### Step 4: Package context

Before prompting, ensure you have:

- [ ] **Goal** — what success looks like
- [ ] **Audience** — who consumes it
- [ ] **Constraints** — length, tone, policy, time
- [ ] **Inputs** — ground truth, reference material
- [ ] **Format** — output structure

See [Context Engineering](context_engineering.md).

### Step 5: Add guardrails

Based on stakes, add appropriate verification:

| Stakes | Guardrails |
|--------|------------|
| Low | Basic sanity check |
| Medium | Ask for assumptions, require sources, human review |
| High | Claim list, source mapping, expert review, audit trail |

### Step 6: Validate

Choose validation methods:

- **Grounding checks** — verify claims in sources
- **Cross-checking** — re-ask with different wording, compare
- **Self-checking** — ask model to critique itself
- **Deterministic checks** — code tests, calculators, constraint validation

## Quick decision guide

```
Task arrives
    ↓
What type? (Transform/Generate/Reason/Compute/Research/Act)
    ↓
What stakes? (Low/Medium/High)
    ↓
What posture? (Draft/Verified/Assured)
    ↓
What pattern? (Single-shot/Thought partnership/Parallel)
    ↓
Package context → Add guardrails → Execute → Validate
```

## Signs you're doing it well

- You consciously choose pattern and posture before prompting
- Low-stakes work moves fast
- High-stakes work has documented verification
- Different task types get different treatment

## Signs you're doing it wrong

- Same approach for everything → Not matching to task
- Spending hours on brainstorming → Over-verification
- Publishing without checking → Under-verification
- Surprised by what goes wrong → Didn't assess stakes correctly

## Quick reference

### Task classification prompt

```text
For this task: [task]

1. What's the dominant type? (Transform/Generate/Reason/Compute/Research/Act)
2. What's at stake if it's wrong?
3. What trust posture fits? (Draft/Verified/Assured)
4. What pattern should I use?
```

### Stakes assessment prompt

```text
If this output is wrong:
- Who is affected?
- What's the worst case?
- How hard is it to fix?

Based on this: Low / Medium / High stakes?
```

---

## Sources

Concepts in this guide are grounded in research and best practices:

- [S0007: OpenAI Prompt Engineering Best Practices](../90_sources/extraction_cards/S0007_openai_prompt_engineering_best_practices.md) — task classification, context packaging
- [S0008: Claude Prompting Best Practices](../90_sources/extraction_cards/S0008_claude_prompting_best_practices.md) — long-horizon planning
- [S0011: OWASP Top 10 for LLMs](../90_sources/extraction_cards/S0011_owasp_llm_top10.md) — risk assessment for AI work
- [S0024: NIST AI RMF](../90_sources/extraction_cards/S0024_nist_ai_rmf.md) — risk management framework

---

## Related

- [Context Engineering](context_engineering.md) — Step 4 in detail
- [Trust Calibration](trust_calibration.md) — Steps 2 and 5 in detail
- [Which pattern?](../decisions/which_pattern.md) — Step 3 decision tree
- [How much verification?](../decisions/how_much_verification.md) — Step 6 guidance
