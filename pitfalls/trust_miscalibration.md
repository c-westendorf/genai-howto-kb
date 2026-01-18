---
title: Trust Miscalibration
updated: 2026-01-17
---

# Trust Miscalibration

## What it looks like

**Over-verification (too slow):**
- Spending hours verifying brainstorming output
- Demanding sources for internal drafts
- Every task gets the same rigorous treatment
- Progress is slow, creativity is killed

**Under-verification (too risky):**
- Publishing without checking claims
- High-stakes work treated like drafts
- Surprised when errors surface later
- "It sounded right" as the only check

## Why it happens

1. **No stakes assessment**: You don't ask "what breaks if this is wrong?"

2. **One-size-fits-all habit**: Same verification for everything.

3. **Trust drift**: Started verified, got lazy over time.

4. **Confidence bias**: Model sounded confident, so you assumed it was right.

5. **Time pressure**: Skipped verification to meet deadline.

## How to fix it

### Quick fix

Ask: "If this is wrong, what breaks?"
- Not much → Iterate fast (TL1)
- Some rework, reputation → Check key claims (TL2)
- Serious harm, hard to fix → Full verification (TL3)

### Full fix

1. **Before every task, assess stakes**
   ```text
   For this task:
   - Who sees this output?
   - What happens if it's wrong?
   - How hard is it to fix?

   Stakes: Low / Medium / High
   ```

2. **Match verification to stakes**

   | Stakes | Verification |
   |--------|--------------|
   | Low | Quick read, basic sanity |
   | Medium | Check 3-5 key claims, human review |
   | High | Full claim list, source mapping, expert review |

3. **Set explicit verification checkpoints**
   - Low: "Read through once before using"
   - Medium: "Verify key claims before sharing"
   - High: "Get [expert] signoff before publishing"

4. **Watch for drift**
   - If you're spending >30 min verifying brainstorming → over-verifying
   - If you're publishing customer content without review → under-verifying

## Prevention

- Always ask "what's at stake?" before starting
- Build verification into your workflow, not as an afterthought
- For teams: agree on what stakes level triggers what process
- Periodically audit: are we verifying appropriately?

## Quick prompts

### To diagnose
```text
For this output:
- What's at stake if it's wrong?
- What verification have I done?
- Is that verification proportional to the stakes?
```

### To right-size (under-verifying)
```text
Before I use this output:
- List the key factual claims
- Which ones should I verify?
- What's the fastest way to verify each?
```

### To right-size (over-verifying)
```text
This is a low-stakes task. I'm going to:
- Read through once for obvious errors
- Check formatting
- Move on

I don't need to: [list what I was about to do but shouldn't]
```

---

## Related

- [Trust Calibration](../concepts/trust_calibration.md) — the underlying concept
- [How much verification?](../decisions/how_much_verification.md) — decision guide
- [Verification checklist](../reference/checklists/verification.md) — when you do need to verify
