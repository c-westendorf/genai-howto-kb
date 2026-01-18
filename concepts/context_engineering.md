---
title: Context Engineering
updated: 2026-01-17
refs: [S0007, S0009, S0012]
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Context Engineering](context_engineering.md) · [Explore → Select → Refine](explore_select_refine.md) · [Trust Calibration](trust_calibration.md) · [Parallel Execution](parallel_execution.md) · [Decision Flow](decision_flow.md) · [One-Shot Planning](oneshot_planning.md)

# Context Engineering

## What it is

Context engineering is packaging the right information so the model can produce a reliable output. The prompt is the smallest part — what matters is the full context: role, task, inputs, constraints, format, and quality bar.

## Why it matters

**If you get this wrong:**
- Outputs are generic, vague, or wrong
- You waste time iterating on symptoms instead of causes
- The model makes up information to fill gaps you left
- You hit [context bloat](../pitfalls/context_bloat.md) — too much noise, not enough signal

**If you get this right:**
- First outputs are already usable
- Iteration is refinement, not rescue
- The model's constraints match yours

## How to apply it

### Step 1: Build a context pack

Before prompting, fill in these six elements:

| Element | Question to answer |
|---------|-------------------|
| **Role** | Who should the model be? (expertise, perspective) |
| **Task** | What exactly should it do? (verb + outcome) |
| **Inputs** | What ground truth is it working with? |
| **Constraints** | What boundaries apply? (length, tone, policy, audience) |
| **Format** | How should output be structured? (bullets, table, JSON) |
| **Quality bar** | What makes "good" output? (rubric, checklist) |

### Step 2: Structure your context

Put elements in this order:

```text
Role: You are a [role].

Task: [specific task with clear outcome].

Inputs (ground truth):
"""
[paste source material here]
"""

Constraints:
- [length]
- [tone]
- [policy]
- [audience]

Output format:
- [structure]

Quality bar:
- [rubric criteria]
```

### Step 3: Separate instructions from data

- Instructions go first
- Data goes in delimited blocks (triple quotes, fences)
- Label external content explicitly

This is both a performance habit and a security habit when handling untrusted content.

### Step 4: Trim ruthlessly

Ask: "What does the model need to know to do this specific task?"

Cut everything else. More context isn't better context — relevant context is.

## Signs you're doing it well

- First outputs need refinement, not rescue
- The model asks clarifying questions about real gaps
- Outputs match your constraints without reminder
- You can reuse the same context pack for similar tasks

## Signs you're doing it wrong

- Outputs are generic or miss the point → You didn't specify enough constraints
- The model invents information → Your inputs don't cover what you asked for
- Outputs get worse as you add more → See [Context Bloat](../pitfalls/context_bloat.md)
- Same prompt works sometimes, fails other times → Your context is ambiguous

## Quick reference

### Context pack template

```text
Role: You are a [role with specific expertise].

Task: [Verb] [specific outcome] for [audience/purpose].

Inputs:
"""
[Paste ground truth — the information to work with]
"""

Constraints:
- Length: [word/page limit]
- Tone: [formal/casual/technical]
- Avoid: [what NOT to include]

Format: [bullets/table/narrative/JSON]

Quality bar:
- [Criterion 1]
- [Criterion 2]
```

### Checklist before prompting

- [ ] Role is specific (not just "helpful assistant")
- [ ] Task is a clear verb + outcome
- [ ] Inputs contain what the model needs (no more, no less)
- [ ] Constraints are explicit (not assumed)
- [ ] Format is specified (not left to model's choice)
- [ ] Quality bar is defined (you'll know if it's good)

---

## Security note

LLMs don't reliably distinguish "data" vs "instructions" in mixed text. When working with untrusted content (emails, webpages, PDFs):

- Quote and label it as **untrusted**
- Constrain outputs to a strict schema
- Run deterministic validation on outputs
- Use least-privilege tool access

See [Security checklist](../reference/checklists/security.md).

---

## Sources

Concepts in this guide are grounded in research and best practices:

- [S0007: OpenAI Prompt Engineering Best Practices](../90_sources/extraction_cards/S0007_openai_prompt_engineering_best_practices.md) — prompt hygiene rules, structuring context
- [S0008: Claude Prompting Best Practices](../90_sources/extraction_cards/S0008_claude_prompting_best_practices.md) — long-horizon prompting, iteration
- [S0009: Microsoft Prompt Engineering Techniques](../90_sources/extraction_cards/S0009_microsoft_prompt_engineering_techniques.md) — supporting content, grounding

---

## Related

- [Explore → Select → Refine](explore_select_refine.md) — the thought partnership loop
- [Context Bloat](../pitfalls/context_bloat.md) — when context engineering goes wrong
- [Context Pack Template](../reference/templates/context_pack.md) — fill-in-the-blank template
- [Context Pack Checklist](../reference/checklists/context_pack.md) — verification checklist
