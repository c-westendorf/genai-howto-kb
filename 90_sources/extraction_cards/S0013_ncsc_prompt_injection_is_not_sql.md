---
title: NCSC — Prompt injection is not SQL injection (it may be worse)
source_id: S0013
type: gov-guidance
authors: David C (NCSC)
published: 2025-12-08
accessed: 2026-01-17
evidence_grade: A
tags:
  - security
  - prompt-injection
  - system-design
url: https://www.ncsc.gov.uk/pdfs/blog-post/prompt-injection-is-not-sql-injection.pdf
---

# Why this matters
This is one of the clearest, practitioner-focused explanations of why prompt injection is not a “simple fix.”

# Key takeaways (operational)
- Prompt injection often happens when developers concatenate **untrusted content** with instructions and assume a boundary.
- LLMs do not enforce a security boundary between **data and instructions** in a prompt.
- The post argues prompt injection may never be “fully mitigated” like SQL injection; treat LLMs as an **inherently confusable deputy** and manage residual risk.
- For tool-using systems, focus on deterministic safeguards and **least privilege**.

# How to incorporate
- Use this as the core reading for the onboarding security module.
- Add a mandatory checklist step: “What’s the worst-case action the system can take if coerced?”

# Suggested links
- Mentions alignment with ETSI TS 104 223 (see S0023)
- Points to design-focused mitigations (see S0021, S0022)
