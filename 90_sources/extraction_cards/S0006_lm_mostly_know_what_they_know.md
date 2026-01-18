---
title: Language Models (Mostly) Know What They Know
source_id: S0006
type: paper
authors: Saurabh R. Kadavath; Aman Arora; Ethan Perez; et al.
published: 2022 (arXiv submitted 2022-07-11)
accessed: 2026-01-17
evidence_grade: A
tags:
  - calibration
  - uncertainty
  - verification
url: https://arxiv.org/abs/2207.05221
---

# Why this matters
A practical pushback technique is asking the model to estimate uncertainty/confidence. This paper studies calibration: when models “know what they know.”

# Key takeaways (operational)
- Larger models can be reasonably calibrated when asked in appropriate formats.
- Confidence estimates can help prioritize verification (high confidence + high stakes still needs checking).

# How to use in prompts
- Ask for a confidence estimate with justification:
  - “Give a probability this is correct and what evidence drives that.”
- Ask for “what would change your mind?” and “what is most uncertain?”

# Limitations
- Confidence can be miscalibrated depending on prompt format and domain.
- Treat confidence as a *signal*, not proof.
