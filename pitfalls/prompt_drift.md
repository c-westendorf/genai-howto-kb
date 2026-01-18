---
title: Prompt Drift
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](index.md) · [Decisions](../decisions/index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Context Bloat](context_bloat.md) · [Trust Miscalibration](trust_miscalibration.md) · [Prompt Drift](prompt_drift.md) · [Generic Outputs](generic_outputs.md) · [Hallucinations](hallucinations.md) · [Getting Stuck](getting_stuck.md)

# Prompt Drift

## What it looks like

- Prompts that used to work now produce different results
- Quality has gradually degraded over time
- You keep adding more context but it doesn't help
- Model seems to interpret instructions differently
- Accumulated edits have made the prompt confusing

## Why it happens

1. **Model updates**: The underlying model changed, subtle behavior shifts.

2. **Accumulated cruft**: Each iteration added "fixes" that now conflict.

3. **Context contamination**: Old context is no longer relevant but still present.

4. **Instruction ambiguity**: What seemed clear no longer is (to the model).

5. **Implicit assumptions**: Your prompt relied on behavior that's no longer default.

## How to fix it

### Quick fix

Strip the prompt to essentials and rebuild:
```text
[Remove everything]

Role: [one line]
Task: [one line]
Key constraint: [one line]
Format: [one line]

Go.
```

### Full fix

1. **Identify what's broken**
   ```text
   This prompt used to work but now produces [problem].

   What I expect: [expected output]
   What I get: [actual output]

   What changed?
   ```

2. **Audit the prompt**
   - Read every line. Is it still necessary?
   - Look for conflicting instructions
   - Look for outdated context
   - Look for implicit assumptions

3. **Rebuild from clean slate**
   - Start with the minimal context pack
   - Add one element at a time
   - Test after each addition
   - Stop when it works (resist adding "just in case" context)

4. **Document what works**
   - Save working prompts as templates
   - Note the model version if relevant
   - Note what the prompt is sensitive to

5. **Make prompts robust**
   - Be explicit about format (don't assume)
   - Be explicit about constraints (don't assume)
   - Use structured templates (less ambiguity)
   - Test with slightly different wording

## Prevention

- Keep prompts as simple as possible
- Document working prompts
- Periodically review and clean prompts
- Don't add context "just in case" — it accumulates
- When editing, ask "can I remove something instead?"

## Quick prompts

### To diagnose
```text
Ignore my previous instructions.

Tell me:
1. What task do you think I'm asking for?
2. What constraints do you see?
3. What's confusing or contradictory?
```

### To clean up
```text
Here's my current prompt: [paste]

This used to work but now produces [problem].

1. What's unclear or contradictory?
2. What can be removed?
3. Suggest a cleaner version.
```

### To test robustness
```text
Rephrase this task three different ways.
Do all three phrasings produce the same output?

Task: [your task]
```

---

## Related

- [Context Engineering](../concepts/context_engineering.md) — how to structure prompts well
- [Context Bloat](context_bloat.md) — a common cause of drift
- [Context pack template](../reference/templates/context_pack.md) — clean starting point
