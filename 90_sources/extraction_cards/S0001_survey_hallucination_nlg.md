---
title: Survey of Hallucination in Natural Language Generation
source_id: S0001
type: paper
authors: Ziwei Ji; Nayeon Lee; Rita Frieske; Tiezheng Yu; Dan Su; Yan Xu; Etsuko Ishii; Yejin Bang; Delong Chen; Wenliang Dai; Ho Shu Chan; Andrea Madotto; Pascale Fung
published: 2022 (last revised 2024-07-14)
venue: ACM Computing Surveys (journal reference noted on arXiv)
accessed: 2026-01-17
evidence_grade: A
tags:
  - hallucination
  - reliability
  - evaluation
  - mitigation
url: https://arxiv.org/abs/2202.03629
---

# Why this matters
Hallucination is a core constraint when using genAI as a thought partner. This survey consolidates what hallucination is, how it is measured, and mitigation approaches across tasks.

# Key takeaways (operational)
- Hallucination is a broad phenomenon that shows up across NLG tasks (summarization, dialogue, QA, data-to-text, MT, vision-language).
- Treat hallucination as a *systems problem*: data, model objectives, decoding, and the surrounding workflow all contribute.
- Mitigation is multi-layered: better evaluation metrics, model training objectives, retrieval/grounding, and post-generation verification.

# Useful taxonomy for our KB
Use these buckets when teaching failure modes:
- **Intrinsic hallucination**: contradicts source input.
- **Extrinsic hallucination**: introduces unsupported info not present in source.
- **Task-dependent variants**: e.g., dialogue “persona drift,” summarization “fact drift,” QA fabrication.

# How to incorporate into the onboarding guide
- Module: *Mental models + limitations*
  - Introduce hallucination taxonomy.
- Module: *Verification behavior*
  - Teach “claims → evidence mapping” as a default habit.

# Limitations / cautions
- This is a broad survey; for operational guidance, pair it with concrete verification playbooks (S0002, S0006) and security guidance (S0013).

# Suggested links
- Extraction complement: S0002 (SelfCheckGPT), S0003 (TruthfulQA), S0004 (HELM)
