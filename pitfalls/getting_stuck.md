---
title: Getting Stuck
updated: 2026-01-17
refs: [S0004, S0006]
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](index.md) · [Decisions](../decisions/index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Context Bloat](context_bloat.md) · [Trust Miscalibration](trust_miscalibration.md) · [Prompt Drift](prompt_drift.md) · [Generic Outputs](generic_outputs.md) · [Hallucinations](hallucinations.md) · [Getting Stuck](getting_stuck.md)

# Getting Stuck

## What it looks like

- The model keeps giving you the same thing
- Iteration isn't improving anything
- You've refined 5+ times with no progress
- The model repeats your words back without adding value
- You don't know what to try next

## Why it happens

1. **The framing is wrong**: You're iterating on the wrong problem definition.

2. **Context is poisoned**: Bad assumptions or wrong information are embedded in the context.

3. **Prompt is over-constrained**: So many constraints that there's no room to explore.

4. **You're asking for refinement when you need reframing**: More polish won't fix a wrong approach.

5. **Model is pattern-matching to your language**: It's reflecting your framing instead of generating new ideas.

## How to fix it

### Quick fix

Reframe entirely:
```text
Forget everything above. If you were starting fresh on [goal],
what's a completely different approach we haven't considered?
```

### When to reset vs. continue

**Reset (new conversation)** when:
- Context is poisoned with wrong assumptions
- You've iterated 5+ times without progress
- The framing was wrong from the start
- You can't remember what's in your context

**Continue iterating** when:
- Each iteration is better than the last
- The problem is specific and fixable
- You'd lose valuable exploration/research

See [Should I Start Over?](../decisions/start_over.md) for the full decision tree.

### Checkpoint restart pattern

Before starting over, capture what's worth keeping:

```text
Before we reset, summarize:
1. What was the original goal?
2. What approaches did we try?
3. What did we learn (including what NOT to do)?
4. What facts/research should we carry forward?
5. What's the refined version of the goal?
```

Then start fresh with a checkpoint:

```text
[NEW CONVERSATION]

Goal: [refined goal from checkpoint]

What we learned from previous attempts:
- Don't do: [failed approaches]
- Carry forward: [useful research/facts]
- Key constraint: [discovered requirement]

Fresh start. What's the best approach?
```

### Try a different model

If stuck with one model, try another:
- Different models have different strengths and failure modes
- A fresh model has no context pollution
- Compare responses to triangulate

See [Multi-LLM Tactics](../decisions/multi_llm.md) for when and how to use multiple models.

### Full fix

1. **Diagnose the stuck state**
   ```text
   We're not making progress. Step back and tell me:
   1. What's the core problem we're trying to solve?
   2. What approaches have we tried?
   3. Why aren't they working?
   4. What's a different frame for this problem?
   ```

2. **Challenge your own framing**
   - Ask: "Am I solving the right problem?"
   - Ask: "What assumptions am I making that might be wrong?"
   - Try stating the opposite of your constraints

3. **Reset the context**
   - Start a new conversation
   - Rebuild context from scratch with only essentials
   - Remove accumulated "helpful" context that's now noise

4. **Force divergence**
   ```text
   Give me 5 approaches that are maximally different from each other.
   At least one should feel counterintuitive or uncomfortable.
   ```

5. **Change the role or perspective**
   ```text
   If a [skeptic / competitor / user / expert in different field]
   looked at this problem, what would they say we're missing?
   ```

6. **Make it falsifiable**
   ```text
   What would prove that our current approach is wrong?
   What would we expect to see if it's working?
   ```

## Prevention

- Don't iterate more than 3-4 times without stepping back
- Periodically ask "are we solving the right problem?"
- Keep context lean — accumulated context causes stuck states
- Use explore/select/refine — don't jump straight to refining

## Quick prompts

### To diagnose
```text
We've tried several iterations.
1. What's the core problem?
2. What have we tried?
3. Why isn't it working?
4. What are we missing?
```

### To escape (reframe)
```text
Forget the specifics of what we've discussed.
The underlying goal is: [goal in one sentence]
What's a completely different way to approach this?
```

### To escape (reset)
```text
Let's start over with a clean slate.
Here's what I need: [minimal task description]
Here's what I know: [essential context only]
What would you do?
```

### To force divergence
```text
We're stuck in one frame. Give me 5 approaches:
1. The obvious approach
2. The opposite of #1
3. How a beginner would approach it
4. How an expert in a different field would approach it
5. The approach that would work if we had unlimited resources
```

### To challenge assumptions
```text
List the assumptions we're making.
Which one is most likely to be wrong?
What changes if we flip that assumption?
```

---

## Related

- [Explore → Select → Refine](../concepts/explore_select_refine.md) — the loop that prevents stuck states
- [Context Bloat](context_bloat.md) — accumulated context causes stuck states
- [When to start over](../decisions/start_over.md) — decision criteria for resetting
