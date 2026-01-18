---
title: Contributing
created: 2026-01-17
---

# Contributing guidelines

## 1) Add a source

1. Create a new extraction card:
   - Copy `/90_sources/source_extraction_template.md`
   - Save to `/90_sources/extraction_cards/S####_short_slug.md`

2. Update `/90_sources/sources_index.md`:
   - Add the source ID, title, year, type, evidence grade, tags

3. Link the source from any synthesis docs:
   - Use a short reference like: `Refs: S####, S####`

## 2) Update synthesis docs

When you update methodology/trust/pushback docs:
- Add a **Changelog** note in `/00_meta/changelog.md`
- Add or update **Refs** sections

## 3) Evidence grading (quick)

- **A**: peer-reviewed paper, formal standard, government guidance
- **B**: preprint from credible lab, official vendor docs
- **C**: reputable industry analysis / security research blog
- **D**: opinion / low signal (use sparingly)
