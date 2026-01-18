---
title: Defeating Prompt Injections by Design (CaMeL)
source_id: S0021
type: paper
authors: Edoardo Debenedetti; Ilia Shumailov; Tianqi Fan; Jamie Hayes; Nicholas Carlini; Daniel Fabian; Christoph Kern; Chongyang Shi; Andreas Terzis; Florian Tramèr
published: 2025 (arXiv submitted 2025-03-24; revised 2025-06-24)
accessed: 2026-01-17
evidence_grade: A
tags:
  - security
  - prompt-injection
  - agents
  - capabilities
url: https://arxiv.org/abs/2503.18813
---

# Why this matters
CaMeL is an example of a *system-layer* defense approach: do not rely on the underlying model to “behave,” enforce safe control/data flow.

# Key takeaways (operational)
- Defense concept: extract **control + data flows** from the trusted query so untrusted retrieved data cannot change program flow.
- Uses a **capability** notion to restrict tool calls and prevent data exfiltration.
- Reports a tradeoff between utility and provable security on an agent benchmark.

# How to incorporate
- Use as an advanced module for builders of tool-using systems.
- Translate into a user-facing principle:
  - “If the model can call tools, you need deterministic guardrails that the model cannot override.”

# Suggested links
- S0013 (NCSC prompt injection framing)
- S0022 (design patterns for securing agents)
