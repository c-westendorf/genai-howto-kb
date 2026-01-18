---
title: HELM: Holistic Evaluation of Language Models
source_id: S0004
type: paper
authors: Rishi Bommasani; Percy Liang; Tony Lee; et al.
published: 2022 (arXiv submitted 2022-11-16)
accessed: 2026-01-17
evidence_grade: A
tags:
  - evaluation
  - benchmarking
  - calibration
  - robustness
url: https://arxiv.org/abs/2211.09110
---

# Why this matters
HELM is a foundational framework for evaluating LLMs across multiple dimensions (not just accuracy).

# Key ideas
- Define **scenarios** (tasks + domains) and evaluate models across them.
- Track many **metrics** simultaneously (e.g., accuracy, calibration, robustness, toxicity, efficiency).
- Publish results transparently so tradeoffs are visible.

# Operational takeaways for a user guide
- Train users to ask: “Which metric matters for this task?”
  - drafting vs correctness vs safety vs latency/cost
- Encourage *multi-metric thinking*: a model can be strong on one axis and weak on another.

# How to incorporate
- Use as conceptual backing for the “Stakes × Uncertainty” framework.
- Use HELM-style thinking to define an internal rubric for outputs.

# Limitations / cautions
- Benchmarks can be gamed. For real work, complement with centaur evaluations (S0016).
