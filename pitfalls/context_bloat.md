---
title: Context Bloat
updated: 2026-01-17
---

# Context Bloat

## What it looks like

- Outputs are getting worse as you add more context
- The model ignores important instructions buried in the middle
- Responses are generic despite detailed input
- The model fixates on irrelevant details
- You're pasting "everything just in case"

## Why it happens

1. **More isn't better**: Models have limited attention. Irrelevant context competes with relevant context.

2. **Signal-to-noise ratio drops**: The important information is diluted by filler.

3. **Lost in the middle**: Models tend to weight the beginning and end of context more heavily. Critical info in the middle gets overlooked.

4. **Fear of omission**: You're afraid to cut anything in case it matters. So everything goes in.

5. **Accumulated cruft**: Each iteration adds more "helpful context" until the whole thing is noise.

## How to fix it

### Quick fix

Cut your context by 50%. Ask: "What does the model need to know to do this specific task?" Remove everything else.

### Full fix

1. **Identify the core task**
   - Write one sentence describing what the model should do
   - If you can't, you're not clear on the task

2. **Audit every piece of context**
   - For each block of context, ask: "Does this directly help with the task?"
   - If no → cut it
   - If maybe → cut it

3. **Structure what remains**
   - Put the most important instructions first
   - Put critical data in delimited blocks
   - Use clear section headers

4. **Test with minimal context**
   - Try the prompt with only essential context
   - Add back only what's proven necessary

5. **Create focused context packs**
   - Different tasks need different context
   - Don't reuse the same mega-context for everything

## Prevention

- Start with less context, add only what's needed
- Ask "would I include this in a brief to a human?" — if no, don't include it
- Separate context for different tasks (don't reuse a giant blob)
- Review context periodically and prune

## Quick prompts

### To diagnose
```text
Before answering, tell me:
1. What task are you being asked to do?
2. What information from the context are you using?
3. What information are you ignoring?
```

### To escape
```text
Let's reset. Ignore everything above this line.

Here's the task: [one sentence]
Here's what you need to know: [minimal context]

Now answer.
```

### To restructure
```text
I'm going to give you context in sections. Focus on sections marked CRITICAL.

CRITICAL - Task:
[task]

CRITICAL - Key inputs:
[inputs]

BACKGROUND (use only if needed):
[background]
```

---

## Related

- [Context Engineering](../concepts/context_engineering.md) — how to structure context well
- [Getting Stuck](getting_stuck.md) — when iteration isn't helping
- [Context pack template](../reference/templates/context_pack.md) — structured template
