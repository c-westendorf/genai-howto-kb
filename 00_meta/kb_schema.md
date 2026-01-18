---
title: Knowledge Base Schema
created: 2026-01-17
---

# Document types

## Source extraction card
Location: `/90_sources/extraction_cards/`

Purpose:
- Capture what a source says, what it implies for practice, and how it maps to onboarding.

Minimum sections:
- Metadata (YAML)
- Summary
- Key claims (w/ notes on evidence strength)
- Actionable takeaways
- Limitations / failure modes
- How to apply (where in KB / onboarding)

## Synthesis doc
Locations:
- `/01_methodology/`
- `/02_trust/`
- `/03_pushback/`
- `/04_onboarding/`
- `/05_playbooks/`

Purpose:
- Translate evidence into an operational method and training content.

Minimum sections:
- Goal
- Method / checklist
- Examples (prompt patterns)
- Refs (source IDs)

# Front matter

Recommended YAML fields:

```yaml
---
title:
created: 2026-01-17
updated: 2026-01-17
status: draft | active | deprecated
tags: [tag1, tag2]
refs: [S0001, S0002]
---
```

# Naming conventions

- `S####_short_slug.md` for sources
- `kebab_case.md` for synthesis docs
