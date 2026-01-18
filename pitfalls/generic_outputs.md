---
title: Generic Outputs
updated: 2026-01-17
---

# Generic Outputs

## What it looks like

- Everything sounds the same — bland, safe, corporate
- Responses could apply to any company, any situation
- No concrete details, examples, or specifics
- Hedging language everywhere ("may," "could," "it depends")
- Feels like reading a template, not a tailored answer

## Why it happens

1. **No specificity in the prompt**: You asked for "a marketing email" not "a marketing email for [specific product] to [specific audience] in [specific tone]."

2. **Model defaults to safe average**: Without constraints, models produce the median of their training data — which is bland.

3. **No examples provided**: The model doesn't know what "good" looks like for you.

4. **No persona or voice**: Default voice is neutral corporate.

5. **Hedging as safety**: Model adds qualifiers to avoid being wrong.

## How to fix it

### Quick fix

Push for specificity:
```text
This is too generic. Rewrite with:
- 3 specific, concrete examples
- No hedging language (remove "may," "could," "might")
- Written as if for [specific audience]
```

### Full fix

1. **Add persona and voice**
   ```text
   Write this as [specific persona] would.
   Tone: [direct/casual/technical/provocative]
   Voice: [confident/informal/expert]
   ```

2. **Demand concrete details**
   ```text
   For every general statement:
   - Add a specific example
   - Include concrete numbers or names
   - Replace abstract with concrete
   ```

3. **Remove hedging**
   ```text
   Remove hedging language. Instead of:
   - "This may help" → "This helps"
   - "You could try" → "Try this"
   - "It depends" → "For [case A], do X. For [case B], do Y."
   ```

4. **Provide examples of good output**
   ```text
   Here's an example of the style I want:
   """
   [paste a specific example]
   """

   Match this style.
   ```

5. **Add constraints that force specificity**
   ```text
   Constraints:
   - Must include 3 specific examples
   - No sentences longer than 15 words
   - Every claim must be tied to a concrete case
   - Must mention [specific product/customer/use case]
   ```

## Prevention

- Always specify persona, tone, and voice
- Always include at least one example
- Explicitly ban hedging language when you don't want it
- Include specific context (names, products, situations)
- Ask for concrete examples as part of the format

## Quick prompts

### To diagnose
```text
On a scale of 1-10, how specific is this output?
1 = could apply to any company
10 = clearly about [our specific situation]

Rate it and explain why.
```

### To fix (inject specificity)
```text
This is too generic. For each paragraph:
1. Add one concrete example
2. Replace one vague word with a specific one
3. Remove one hedge word
```

### To fix (change voice)
```text
Rewrite this in the voice of [specific persona].

This persona:
- Uses short, direct sentences
- Never hedges
- Always gives specific examples
- Speaks from experience, not theory
```

### To fix (add edge cases)
```text
This is the happy path. Now add:
1. What could go wrong
2. Edge cases to watch for
3. Specific situations where this advice doesn't apply
```

---

## Related

- [Context Engineering](../concepts/context_engineering.md) — specify what you want
- [Explore → Select → Refine](../concepts/explore_select_refine.md) — push for better in refine phase
- [Refine prompts](../reference/prompts/refine.md) — prompts for improving output
