---
title: Self-Consistency Improves Chain-of-Thought Reasoning
source_id: S0005
type: paper
authors: Xuezhi Wang; Jason Wei; Dale Schuurmans; Quoc V. Le; Ed Chi; Denny Zhou
published: 2022 (arXiv submitted 2022-03-22)
accessed: 2026-01-17
evidence_grade: A
tags:
  - reasoning
  - verification
  - sampling
url: https://arxiv.org/abs/2203.11171
---

# Why this matters
Many failures are “single-chain failures” where one reasoning path goes wrong. Self-consistency mitigates this by sampling multiple reasoning paths.

# Core idea
Sample multiple chains of thought and select the most consistent final answer (marginalize over reasoning paths).

# Operational takeaways
- For reasoning problems, run **multiple independent attempts**.
- If answers diverge, treat as a risk signal and investigate assumptions or missing context.

# Practical workflow
1. Ask for 3 independent solutions.
2. Compare answers and reconcile.
3. Verify the final.

# Limitations
- Can be consistently wrong.
- Requires multiple samples (cost).

# Suggested links
- Pair with S0002 (SelfCheckGPT) for factuality screening.
