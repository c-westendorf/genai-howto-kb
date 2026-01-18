---
title: Ragas: Automated Evaluation of Retrieval Augmented Generation
source_id: S0010
type: paper
authors: Shahul Es; Jithin James; Luis Espinosa-Anke; Steven Schockaert
published: 2023 (arXiv submitted 2023-09-26; revised 2025-04-28)
accessed: 2026-01-17
evidence_grade: B
tags:
  - RAG
  - evaluation
  - grounding
url: https://arxiv.org/abs/2309.15217
---

# Why this matters
If you use Retrieval-Augmented Generation (RAG) to reduce hallucinations, you still need to **measure** whether retrieval + generation is behaving well.

# Key takeaways (operational)
- RAG evaluation is multi-dimensional: retrieval quality and generation faithfulness both matter.
- Ragas proposes **reference-free metrics** to evaluate RAG systems without needing ground-truth labels.
- A metric suite can speed up iteration cycles when changing chunking, embedding models, retrievers, prompts, and rerankers.

# How to incorporate
- In the guide, use Ragas as a template for “evaluate the pipeline, not just the answer.”
- Teach a practical RAG triage:
  1) Are retrieved passages relevant/focused?
  2) Does the answer stay faithful to retrieved passages?
  3) Is the final output useful and well-formed?

# Limitations / cautions
- Metrics are proxies. For high-stakes use, combine automated evaluation with spot-checking and domain review.

# Suggested links
- Pair with S0002 (SelfCheckGPT) for black-box self-checking.
