---
title: Quick Reference
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](../playbooks/index.md) · [Reference](index.md)

# Quick Reference

Copy-paste prompts, checklists, and templates. Linked from throughout the guide.

---

## Prompts

### By phase
- [Explore prompts](prompts/explore.md) — "Give me 5 different approaches to..."
- [Select prompts](prompts/select.md) — "Compare these options against criteria..."
- [Refine prompts](prompts/refine.md) — "Critique this and suggest improvements..."

### For verification
- [Pushback prompts](prompts/pushback.md) — "What assumptions are you making?"
- [Verification prompts](prompts/verification.md) — "List your claims and evidence..."

---

## Checklists

- [Context pack checklist](checklists/context_pack.md) — Is your context complete?
- [Verification checklist](checklists/verification.md) — Is this output trustworthy?
- [Output quality checklist](checklists/output_quality.md) — Is this good enough?
- [Security checklist](checklists/security.md) — Is this safe to use?

---

## Templates

- [Context pack template](templates/context_pack.md) — Universal fill-in-the-blank
- [Options table template](templates/options_table.md) — Compare alternatives
- [Evidence table template](templates/evidence_table.md) — Map claims to sources
- [GSD task spec template](templates/gsd_task_spec.md) — GenAI-friendly task specs with `...` expansion markers
- [RALPH state files](templates/ralph_state_files.md) — State files for context-clean execution loops

---

## Most used

**For exploring options:**
```
Give me 5 meaningfully different approaches to [task].
For each, describe the approach, its strengths, its weaknesses, and when you'd use it.
```

**For pushing back:**
```
What assumptions are you making? List them explicitly.
Which of these assumptions is most likely to be wrong?
```

**For verification:**
```
List the factual claims you just made.
For each claim, rate your confidence (high/medium/low) and explain why.
```

**For getting unstuck:**
```
We're not making progress. Step back and tell me:
1. What's the core problem we're trying to solve?
2. What have we tried that didn't work?
3. What's a completely different approach we haven't considered?
```
