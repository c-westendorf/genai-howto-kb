---
title: NCSC — Exercise caution when building off LLMs
source_id: S0014
type: gov-guidance
authors: David C (NCSC)
published: 2023-08-30
accessed: 2026-01-17
evidence_grade: A
tags:
  - security
  - risk
  - model-change
url: https://www.ncsc.gov.uk/pdfs/blog-post/exercise-caution-building-off-llms.pdf
---

# Why this matters
Operational reality: models and APIs change. Prompts that “work today” can degrade tomorrow.

# Key takeaways (operational)
- Treat LLM understanding as “in beta”: capabilities and vulnerabilities are still being mapped.
- Account for vendor/API churn and model updates breaking prompts.
- Architect systems around worst-case behavior, especially if the system can take actions.

# How to incorporate
- Add a guide section: “Operational resilience for prompts” (versioning, regression tests, monitoring).

# Suggested links
- S0013 (prompt injection risk framing)
