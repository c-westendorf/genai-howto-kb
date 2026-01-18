---
title: OWASP LLM01 Prompt Injection
source_id: S0012
type: standard
authors: OWASP Project (community)
published: 2024 (version varies)
accessed: 2026-01-17
evidence_grade: A
tags:
  - security
  - prompt-injection
  - threat-model
url: https://raw.githubusercontent.com/OWASP/www-project-top-10-for-large-language-model-applications/main/2_0_vulns/LLM01_PromptInjection.md
---

# Why this matters
Prompt injection is a core “failure mode” when genAI is used as a reasoning layer over untrusted text or when it can trigger tools.

# Key takeaways (operational)
- Prompt injection can be direct (user input) or indirect (content from webpages/emails/docs).
- Mitigations are layered: input handling, instruction/data separation, tool constraints, and deterministic validation.

# How to incorporate
- Add a standard “untrusted input” warning to all templates that process external text.
- Teach “least privilege for tools” and schema validation as default architecture.

# Limitations / cautions
- No single prompt trick fully solves injection; treat it as a system design problem.

# Suggested links
- S0013 (NCSC prompt injection: inherently confusable deputy)
- S0020 (Indirect prompt injection paper)
