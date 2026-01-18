---
title: Pitfalls & Fixes
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](index.md) · [Decisions](../decisions/index.md) · [Playbooks](../playbooks/index.md) · [Reference](../reference/index.md)

# Pitfalls & Fixes

Common traps and how to escape them. Each pitfall includes symptoms, root cause, fixes, and copy-paste prompts.

---

## [Context Bloat](context_bloat.md)

You're pasting everything in and outputs are getting worse. The model is drowning in noise.

**Quick fix**: Cut context by 50%. Keep only what directly answers "what does the model need to know to do this specific task?"

---

## [Hallucination Traps](hallucinations.md)

The output sounds confident but is fabricated. Citations don't exist. Numbers are made up. Claims are false.

**Quick fix**: Ask "List the factual claims you just made and rate your confidence in each. Which ones are you uncertain about?"

---

## [Getting Stuck](getting_stuck.md)

The model keeps giving you the same thing, or you don't know how to proceed. Iteration isn't improving anything.

**Quick fix**: Reframe the task entirely. "Forget everything. If you were starting fresh on [goal], what would you do differently?"

---

## [Trust Miscalibration](trust_miscalibration.md)

You're over-verifying low-stakes work (slow) or under-verifying high-stakes work (risky). Your effort doesn't match the stakes.

**Quick fix**: Ask "If this is wrong, what breaks?" If the answer is "not much," iterate fast. If the answer is serious, slow down.

---

## [Prompt Drift](prompt_drift.md)

Your prompts used to work but don't anymore. Model updates, context changes, or accumulated cruft.

**Quick fix**: Strip the prompt to essentials. Rebuild from a clean context. Test with fresh examples.

---

## [Generic Outputs](generic_outputs.md)

Everything sounds the same — bland, safe, corporate. The model is giving you the average of its training data.

**Quick fix**: Demand specificity. "Give me the version that [specific persona] would write. Include concrete details, not generalities."

---

## Using this section

1. **Identify the symptom** — what's going wrong?
2. **Read the root cause** — why is this happening?
3. **Try the quick fix** — often enough to get unstuck
4. **Apply the full fix** — if the problem persists
5. **Use prevention** — avoid it next time

Each pitfall links back to the relevant [concept](../concepts/index.md) so you can build the underlying skill.

---

## Related

- [Core Concepts](../concepts/index.md) — the skills that prevent pitfalls
- [Decision Support](../decisions/index.md) — when you need help deciding
- [Verification Checklist](../reference/checklists/verification.md) — catch issues before they're pitfalls
- [Glossary](../00_meta/glossary.md) — key terms defined
