---
title: Glossary
created: 2026-01-17
updated: 2026-01-17
---

# Glossary

Key terms used throughout this guide.

---

## Core concepts

- **Thought partnership**: Using genAI to co-think (explore options, select with criteria, refine iteratively) rather than treating it as a vending machine that produces final answers. See [Explore → Select → Refine](../concepts/explore_select_refine.md).

- **Context engineering**: The practice of deliberately structuring what you give the model — role, task, inputs, constraints, format, quality bar — to get reliable outputs. The prompt is the smallest part; context is everything. See [Context Engineering](../concepts/context_engineering.md).

- **Context pack**: A structured bundle of context containing role, task, inputs, constraints, format, and quality bar. The reusable unit of context engineering.

- **Explore → Select → Refine**: The three-phase thought partnership loop. Explore generates options (diverge), Select evaluates against criteria (converge), Refine iterates to quality bar (polish). See [Explore → Select → Refine](../concepts/explore_select_refine.md).

- **Trust calibration**: Matching verification intensity to stakes. Low stakes = iterate fast (TL1). Medium stakes = verify key claims (TL2). High stakes = rigorous verification, expert review (TL3). See [Trust Calibration](../concepts/trust_calibration.md).

- **Trust levels (TL0-TL3)**: A framework for matching verification effort to risk:
  - TL0: Zero trust (adversarial context)
  - TL1: Iterate and spot-check (low stakes)
  - TL2: Verify claims and cross-reference (medium stakes)
  - TL3: Full verification, expert review (high stakes)

- **Parallel execution**: Running multiple genAI threads concurrently to increase throughput, reduce fixation, and merge diverse perspectives. Patterns include branch-and-merge, multi-role team, generator-critic-editor, and decompose-and-farm. See [Parallel Execution](../concepts/parallel_execution.md).

- **Decision flow**: The meta-question sequence: What kind of task? → What's at stake? → What trust posture? → What pattern? → How much context? → What guardrails? → How to validate? See [Decision Flow](../concepts/decision_flow.md).

---

## Verification and trust

- **Groundedness**: Whether claims are supported by provided context or verifiable sources. A grounded response doesn't add unsupported information.

- **Hallucination**: Model output that is fluent but not grounded in truth or provided context. Types include fabrication, false specificity, conflation, outdatedness, and citation hallucination. See [Hallucinations](../pitfalls/hallucinations.md).

- **Intrinsic hallucination**: Output that contradicts the source input provided.

- **Extrinsic hallucination**: Output that introduces information not present in or supported by the source.

- **Calibration**: Whether expressed confidence aligns with actual correctness. Well-calibrated models are uncertain when they should be.

- **Verification**: The process of checking genAI output before trusting it. Intensity should match stakes. See [Verification Checklist](../reference/checklists/verification.md).

---

## Common problems

- **Context bloat**: When excessive, redundant, or poorly structured context degrades output quality. Signs: outputs ignore recent context, responses become generic, contradictions appear. See [Context Bloat](../pitfalls/context_bloat.md).

- **Prompt drift**: When prompts that used to work stop working, due to accumulated cruft, model updates, or changed requirements. See [Prompt Drift](../pitfalls/prompt_drift.md).

- **Generic outputs**: Bland, safe, corporate-sounding outputs that lack specificity or voice. Usually caused by insufficient context or over-hedging. See [Generic Outputs](../pitfalls/generic_outputs.md).

- **Trust miscalibration**: Over-verifying low-stakes work (slow) or under-verifying high-stakes work (risky). See [Trust Miscalibration](../pitfalls/trust_miscalibration.md).

- **Getting stuck**: When iteration produces diminishing returns or the same unsatisfactory output. Requires reframing or reset. See [Getting Stuck](../pitfalls/getting_stuck.md).

---

## Patterns and techniques

- **Single-shot**: One prompt, one response, done. Appropriate for simple, low-stakes tasks.

- **Few-shot prompting**: Providing examples of desired input-output pairs to guide the model's behavior.

- **Chain-of-thought (CoT)**: Asking the model to show its reasoning step by step, which often improves accuracy on complex tasks.

- **Branch-and-merge**: A parallel execution pattern where you generate multiple solutions, then merge the best elements.

- **Generator-critic-editor**: A parallel execution pattern with three roles: one generates, one critiques, one synthesizes.

- **Decompose-and-farm**: A parallel execution pattern where you break a task into independent subtasks and run them in parallel.

- **Pre-mortem**: Imagining a future failure and working backward to identify what could cause it. Useful for stress-testing decisions.

- **Red team**: Deliberately trying to find flaws, vulnerabilities, or weaknesses in an output or system.

- **BLUF (Bottom Line Up Front)**: Communication pattern where the key message comes first, followed by supporting details.

---

## Security

- **Prompt injection**: Attacks or failures where untrusted input alters model behavior, especially when the model can take actions. See [Security Checklist](../reference/checklists/security.md).

- **Indirect prompt injection**: Prompt injection via content the model retrieves or processes (emails, documents, web pages) rather than direct user input.

- **Confused deputy**: Security framing where the model can be coerced to act on untrusted data because it does not separate instructions from data.

- **RAG (Retrieval-Augmented Generation)**: Supplying retrieved documents or knowledge as context for generation. Improves grounding but introduces injection surface.

---

## Roles and evolution

- **L1 (Transactional)**: User treats genAI as a search engine — single prompts, accepts first answer.

- **L2 (Structured)**: User provides structured context, iterates, gets better outputs.

- **L3 (Thought Partner)**: User runs explore/select/refine consciously, calibrates trust to stakes.

- **L4 (Scaled Operator)**: User employs parallel execution, creates reusable templates, teaches others.

See [Evolution Map](../evolution.md) for the full progression.

---

## Related

- [Core Concepts](../concepts/index.md)
- [Pitfalls & Fixes](../pitfalls/index.md)
- [Quick Reference](../reference/index.md)
