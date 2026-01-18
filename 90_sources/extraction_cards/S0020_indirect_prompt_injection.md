---
title: Not what you've signed up for: Indirect Prompt Injection (LLM-Integrated Applications)
source_id: S0020
type: paper
authors: Kai Greshake; Sahar Abdelnabi; Shailesh Mishra; Christoph Endres; Thorsten Holz; Mario Fritz
published: 2023 (arXiv submitted 2023-02-23)
accessed: 2026-01-17
evidence_grade: A
tags:
  - security
  - prompt-injection
  - indirect-injection
url: https://arxiv.org/abs/2302.12173
---

# Why this matters
This paper shows how *content you retrieve* (web pages, documents, etc.) can act like attacker-controlled instructions when fed into an LLM-based app.

# Key takeaways (operational)
- LLM-integrated apps blur the line between **data and instructions**, enabling *indirect prompt injection*.
- Attackers can inject prompts into data likely to be retrieved, without directly interacting with the system.
- The paper presents a security taxonomy and shows practical viability against real systems.
- The authors argue effective mitigations are still limited.

# How to incorporate
- In onboarding, teach that “untrusted documents are executable instructions unless the system prevents it.”
- In system design, emphasize:
  - strict data/instruction separation
  - tool sandboxing + least privilege
  - deterministic validators for actions

# Suggested links
- S0013 (NCSC: inherently confusable deputy framing)
- S0021 / S0022 (design patterns and capability-based defenses)
