---
title: Select Prompts
updated: 2026-01-17
---

# Select Prompts

Use these during the **select phase** to converge and choose.

---

## Core select prompt

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
```

---

## With trade-off analysis

```text
Compare these options: [list options]

Create a comparison table:
| Option | [Priority 1] | [Priority 2] | [Priority 3] | Risk |

Then recommend which to choose and why.
```

---

## With implementation plan

```text
We're going with: [selected approach]

Give me:
1. Success criteria (measurable)
2. Next 3 concrete steps
3. What could go wrong and how to mitigate
4. What we should check after step 1
```

---

## Break a tie

```text
I can't decide between [option A] and [option B].

1. What's the key differentiator?
2. What information would make the choice obvious?
3. If I had to decide in 5 minutes, which should I pick and why?
4. What's the cost of choosing wrong for each option?
```

---

## Validate the choice

```text
I'm leaning toward: [approach]

Play devil's advocate:
1. Why might this be the wrong choice?
2. What am I not seeing?
3. What would make me regret this?
4. If this fails, what's most likely cause?
```

---

## Commit with criteria

```text
Decision: We're going with [approach]

Confirm:
1. What are we optimizing for?
2. What are we trading off?
3. How will we know this is working?
4. When should we reconsider this decision?
```

---

## When to use each

| Prompt | Use when |
|--------|----------|
| Core select | Have clear options and priorities |
| Trade-off analysis | Need structured comparison |
| With implementation plan | Ready to move forward |
| Break a tie | Options seem equally good |
| Validate the choice | Want to stress-test before committing |
| Commit with criteria | Making it official |

---

## Related

- [Explore → Select → Refine](../../concepts/explore_select_refine.md) — the full loop
- [Explore prompts](explore.md) — previous phase
- [Refine prompts](refine.md) — next phase
