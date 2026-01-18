---
title: TruthfulQA: Measuring How Models Mimic Human Falsehoods
source_id: S0003
type: paper
authors: Stephanie Lin; Jacob Hilton; Owain Evans
published: 2021 (arXiv submitted 2021-09-16)
accessed: 2026-01-17
evidence_grade: A
tags:
  - truthfulness
  - hallucination
  - evaluation
url: https://arxiv.org/abs/2109.07958
---

# Why this matters
TruthfulQA operationalizes a key user problem: models can produce fluent answers that match human misconceptions rather than truth.

# Key takeaways (operational)
- “More capable” models can still be untruthful on adversarial or misconception-driven questions.
- Truthfulness is not guaranteed by scale alone.
- Evaluation needs to test *deceptively plausible* failure modes, not only standard QA accuracy.

# How to incorporate
- In onboarding, use TruthfulQA as the canonical motivation for verification behavior.
- Teach learners to ask:
  - “What would make this answer false?”
  - “What assumptions are hidden?”
  - “What sources support this claim?”

# Limitations / cautions
- Benchmark questions are a slice of the problem; real-world work includes context, partial ground truth, and interactive refinement.

# Suggested links
- Pair with S0004 (HELM) for multi-metric evaluation.
