---
title: SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection
source_id: S0002
type: paper
authors: Potsawee Manakul; Adian Liusie; Mark J. F. Gales
published: 2023 (EMNLP 2023; arXiv last revised 2023-10-11)
accessed: 2026-01-17
evidence_grade: A
tags:
  - hallucination
  - verification
  - self-check
  - sampling
url: https://arxiv.org/abs/2303.08896
---

# Why this matters
For many real-world workflows you cannot access model probabilities or internal states. SelfCheckGPT is a black-box approach to detect hallucinations by sampling.

# Core idea
If the model “knows” a fact, repeated samples tend to be consistent. Hallucinations diverge across samples.

# Key takeaways (operational)
- Use **multi-sample consistency** as a *screening test* for factuality.
- Apply at the sentence level (detect likely non-factual sentences) and at the passage level (rank overall factuality).
- Best used as a triage signal: “which parts require verification?”

# How to use in a user workflow
1. Generate an answer.
2. Sample N alternative answers (or paraphrases).
3. Ask the model (or a checker) to compare and flag contradictions.
4. Verify flagged claims with external sources.

# Limitations / cautions
- Consistency ≠ truth. A model can be consistently wrong.
- Sampling increases cost and latency.

# Suggested incorporation
- Add to `/02_trust/verification_playbook.md` as a “self-checking filter.”
