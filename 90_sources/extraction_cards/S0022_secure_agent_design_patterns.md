---
title: Design Patterns for Securing LLM Agents against Prompt Injections
source_id: S0022
type: paper
authors: Luca Beurer-Kellner; Beat Buesser; Ana-Maria Creţu; Edoardo Debenedetti; Daniel Dobos; Daniel Fabian; Marc Fischer; David Froelicher; Kathrin Grosse; Daniel Naeff; Ezinwanne Ozoani; Andrew Paverd; Florian Tramèr; Václav Volhejn
published: 2025 (arXiv submitted 2025-06-10; revised 2025-06-27)
accessed: 2026-01-17
evidence_grade: A
tags:
  - security
  - prompt-injection
  - agents
  - design-patterns
url: https://arxiv.org/abs/2506.08837
---

# Why this matters
Moves the conversation from “prompt tricks” to **agent architecture** patterns with explicit security/utility tradeoffs.

# Key takeaways (operational)
- Proposes principled design patterns for building agents with provable resistance to prompt injection.
- Emphasizes tool access + sensitive data handling as the danger zone.
- Focuses on tradeoffs: you may reduce agent capability to get stronger guarantees.

# How to incorporate
- For advanced onboarding: teach a 2-track model:
  - *user practices* (schemas, verification)
  - *system practices* (capabilities, sandboxing, deterministic validators)

# Suggested links
- S0021 (CaMeL)
- S0013 (NCSC prompt injection)
