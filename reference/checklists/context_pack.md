---
title: Context Pack Checklist
updated: 2026-01-17
---

# Context Pack Checklist

Use before prompting to ensure your context is complete and structured.

---

## Essential elements

- [ ] **Role** is specific
  - Not "helpful assistant"
  - Includes relevant expertise
  - Example: "senior data scientist specializing in experimentation"

- [ ] **Task** is clear
  - Starts with a verb
  - Specifies the outcome
  - Example: "Compare these options and recommend one"

- [ ] **Inputs** are provided
  - Contains what the model needs
  - Doesn't contain irrelevant noise
  - Is clearly delimited (quotes, fences)

- [ ] **Constraints** are explicit
  - Length specified
  - Tone specified
  - Audience named
  - What to avoid stated

- [ ] **Format** is specified
  - Structure is clear (bullets, table, JSON, narrative)
  - Example of good output shown (if complex)

- [ ] **Quality bar** is defined
  - Criteria for "good enough"
  - You'll know it when you see it

---

## Quick check

| Element | Check | If missing... |
|---------|-------|---------------|
| Role | Who should the model be? | Output will be generic |
| Task | What exactly should it do? | Output will be unfocused |
| Inputs | What does it work with? | Model will guess or hallucinate |
| Constraints | What limits apply? | Model will make assumptions |
| Format | How should output look? | Format will vary unpredictably |
| Quality bar | What's "good enough"? | Can't tell if output is done |

---

## Red flags

Watch for these before prompting:

- [ ] No constraints specified (relying on model to guess)
- [ ] Too much context (everything "just in case")
- [ ] Vague task ("help me with..." instead of specific verb)
- [ ] Missing inputs (asking about things not in context)
- [ ] No quality bar (you'll "know it when you see it" — you won't)

---

## Template reminder

```text
Role: [specific expertise]
Task: [verb + outcome]
Inputs: """[ground truth]"""
Constraints: [length, tone, avoid, must-include]
Format: [structure, example]
Quality bar: [criteria]
```

See [full template](../templates/context_pack.md) for details.

---

## Related

- [Context Engineering](../../concepts/context_engineering.md) — the underlying concept
- [Context pack template](../templates/context_pack.md) — fill-in-the-blank version
- [Context Bloat](../../pitfalls/context_bloat.md) — when there's too much
