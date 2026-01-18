---
title: Sources Index
created: 2026-01-17
updated: 2026-01-17
---

# Sources Index

This index lists curated sources backing the [GenAI Usage Guide](../START_HERE.md).

Each concept, pitfall, and pattern in the guide is grounded in peer-reviewed research, official documentation, or established best practices. Sources are referenced in concept files via `refs:` frontmatter and linked in "Sources" sections.

## How sources are used

| Source type | Evidence grade | How used in guide |
|-------------|----------------|-------------------|
| Peer-reviewed papers | A | Core concepts, verification methods |
| Standards (OWASP, NIST, ETSI) | A | Security, risk frameworks |
| Government guidance | A | Security, compliance |
| Official vendor docs | B | Prompting patterns, context engineering |
| Educational resources | C | Onboarding, practical techniques |

---

Evidence grades:
- **A**: peer-reviewed paper, formal standard, government guidance
- **B**: credible preprint, official vendor docs
- **C**: reputable industry analysis / educational resource
- **D**: opinion/low-signal

## Index (v0.1)

| Source ID | Year | Type | Evidence | Title (short) | Tags | Local card |
|---|---:|---|:---:|---|---|---|
| S0001 | 2022 | paper | A | Survey of Hallucination in Natural Language Generation (arXiv:2202.03629) | hallucination, taxonomy, evaluation | /90_sources/extraction_cards/S0001_survey_hallucination_nlg.md |
| S0002 | 2023 | paper | A | SelfCheckGPT (arXiv:2303.08896) | hallucination, self-check, sampling | /90_sources/extraction_cards/S0002_selfcheckgpt.md |
| S0003 | 2021 | paper | A | TruthfulQA (arXiv:2109.07958) | truthfulness, evaluation | /90_sources/extraction_cards/S0003_truthfulqa.md |
| S0004 | 2022 | paper | A | HELM (arXiv:2211.09110) | evaluation, metrics, calibration | /90_sources/extraction_cards/S0004_helm.md |
| S0005 | 2022 | paper | A | Self-Consistency improves Chain-of-Thought Reasoning (arXiv:2203.11171) | reasoning, sampling | /90_sources/extraction_cards/S0005_self_consistency_cot.md |
| S0006 | 2022 | paper | A | Language Models (Mostly) Know What They Know (arXiv:2207.05221) | calibration, uncertainty | /90_sources/extraction_cards/S0006_lm_mostly_know_what_they_know.md |
| S0007 | 2024 | official-doc | B | OpenAI prompt engineering best practices | prompting, context | /90_sources/extraction_cards/S0007_openai_prompt_engineering_best_practices.md |
| S0008 | 2024 | official-doc | B | Claude prompting best practices | prompting, long-horizon | /90_sources/extraction_cards/S0008_claude_prompting_best_practices.md |
| S0009 | 2024 | official-doc | B | Microsoft prompt engineering techniques | prompting, supporting-content | /90_sources/extraction_cards/S0009_microsoft_prompt_engineering_techniques.md |
| S0010 | 2023 | paper | B | Ragas: Automated Evaluation of RAG (arXiv:2309.15217) | RAG, evaluation | /90_sources/extraction_cards/S0010_ragas.md |
| S0011 | 2024 | standard | A | OWASP Top 10 for LLM Applications | security, risk | /90_sources/extraction_cards/S0011_owasp_llm_top10.md |
| S0012 | 2024 | standard | A | OWASP LLM01 Prompt Injection (raw markdown) | security, prompt-injection | /90_sources/extraction_cards/S0012_owasp_llm01_prompt_injection.md |
| S0013 | 2025 | gov-guidance | A | NCSC: Prompt injection is not SQL injection (PDF) | security, prompt-injection | /90_sources/extraction_cards/S0013_ncsc_prompt_injection_is_not_sql.md |
| S0014 | 2023 | gov-guidance | A | NCSC: Exercise caution when building off LLMs (PDF) | security, risk | /90_sources/extraction_cards/S0014_ncsc_exercise_caution_llms.md |
| S0015 | 2023 | gov-guidance | A | NCSC: Thinking about the security of AI systems (PDF) | security, ML, supply-chain | /90_sources/extraction_cards/S0015_ncsc_security_ai_systems.md |
| S0016 | 2025 | paper | B | Centaur Evaluations (Stanford/ICML 2025) | human+AI, evaluation | /90_sources/extraction_cards/S0016_centaur_evaluations.md |
| S0017 | 2023 | paper | C | The Centaur Programmer (arXiv:2304.11172) | human+AI, workflow | /90_sources/extraction_cards/S0017_centaur_programmer.md |
| S0018 | 2024 | edu-resource | C | Mollick: Prompting AI Learner Guide (PDF) | prompting, iteration | /90_sources/extraction_cards/S0018_mollick_prompting_learner_guide.md |
| S0019 | 2024 | edu-resource | C | Mollick/Mollick: Student Exercises (CC BY) | exercises, onboarding | /90_sources/extraction_cards/S0019_mollick_student_exercises.md |
| S0020 | 2023 | paper | A | Indirect prompt injection (arXiv:2302.12173) | security, prompt-injection | /90_sources/extraction_cards/S0020_indirect_prompt_injection.md |
| S0021 | 2025 | paper | A | Defeating prompt injections by design (CaMeL) (arXiv:2503.18813) | security, architecture | /90_sources/extraction_cards/S0021_defeating_prompt_injections_by_design.md |
| S0022 | 2025 | paper | A | Design patterns for securing LLM agents (arXiv:2506.08837) | security, agents | /90_sources/extraction_cards/S0022_secure_agent_design_patterns.md |
| S0023 | 2025 | standard | A | ETSI TS 104 223 baseline cybersecurity requirements for AI models/systems | security, standard | /90_sources/extraction_cards/S0023_etsi_ts_104_223.md |
| S0024 | 2023 | standard | A | NIST AI RMF 1.0 | risk, governance | /90_sources/extraction_cards/S0024_nist_ai_rmf.md |
| S0025 | 2025 | gov-guidance | A | EU: Guidelines for providers of GPAI models | compliance, transparency | /90_sources/extraction_cards/S0025_eu_gpai_guidelines.md |
