---
title: Parallel Execution
updated: 2026-01-17
refs: [S0015, S0016, S0008]
---

# Parallel Execution

## What it is

Running multiple cognitive threads at once, then merging the best parts. Instead of one conversation, one perspective — you get multiple approaches, critiques, or drafts simultaneously.

This scales:
- **Breadth** — more options to choose from
- **Depth** — more critique and stress-testing
- **Speed** — more drafts faster
- **Quality** — more checking and triangulation

## Why it matters

**If you only use single-thread:**
- You're stuck with one perspective
- Errors compound without independent checking
- You miss alternative approaches
- High-stakes work lacks triangulation

**If you use parallel execution:**
- Multiple perspectives catch different things
- Errors are more likely to be caught
- Best parts of each thread can be merged
- Complex work gets proper coverage

## How to apply it

### Pattern 1: Branch and Merge

Generate multiple independent solutions, then combine the best.

**When to use:** You need breadth — multiple approaches to compare.

**Template:**
```text
Generate 4 independent solutions to: [task]

Keep them clearly separated and labeled (A, B, C, D).

Then:
1. Create a merged solution that takes the best parts of each
2. Critique the merged solution
3. Produce an improved final version
```

**Flow:** Generate → Merge → Critique → Final

### Pattern 2: Multi-Role Team

Simulate different roles working on the same problem.

**When to use:** Complex deliverables that need diverse expertise.

**Roles:**
- **Strategist**: Picks approach and trade-offs
- **Researcher**: Finds sources and evidence
- **Writer**: Produces the artifact
- **Reviewer**: Red-teams for correctness and risks

**Template:**
```text
Act as a team with these roles:
- Strategist
- Researcher
- Writer
- Reviewer

For this task: [task]

1. Each role produces its output
2. Then consolidate into one final deliverable
3. Reviewer provides final critique
```

### Pattern 3: Generator → Critic → Editor (GCE)

Three-pass workflow for quality iteration.

**When to use:** You need depth — thorough critique and polish.

**Roles:**
- **Generator**: Produce draft
- **Critic**: Find weaknesses, missing steps, hallucinations
- **Editor**: Rewrite cleanly + add validation checklist

**Template:**
```text
Pass 1 - Generator:
Create a draft for: [task]

Pass 2 - Critic:
Review the draft. Identify:
- Weaknesses
- Missing pieces
- Potential errors
- Unclear sections

Pass 3 - Editor:
Rewrite to address all critic feedback.
Add a validation checklist at the end.
```

### Pattern 4: Decompose and Farm-Out

Break work into independent subtasks, process separately, merge.

**When to use:** Large tasks with natural divisions.

**Examples:**
- Outline + examples + counterarguments
- Research + synthesis + citations
- Spec + test cases + edge cases
- Sections of a document

**Template:**
```text
Break this task into independent subtasks: [task]

For each subtask:
- Complete it independently
- Note any dependencies or connections

Then merge into a coherent whole.
Check for consistency across subtasks.
```

## Guardrails for parallel work

Parallelism increases surface area for errors. Mitigate by:

1. **Keep subtasks independent** — minimize coupling
2. **Use a shared source of truth** — facts and constraints that all threads reference
3. **Require citations for claims** — especially when merging
4. **Cross-check at merge** — look for inconsistencies between threads
5. **Match verification to stakes** — parallel doesn't mean unverified

## Signs you're doing it well

- Merged output is better than any single thread
- Different threads catch different issues
- You can explain what each thread contributed
- Complex work feels manageable

## Signs you're doing it wrong

- Threads produce nearly identical outputs → Not truly parallel, need more divergence
- Merged output is incoherent → Subtasks weren't independent enough
- Errors slip through → Add verification at merge step
- Taking longer than single-thread → Task didn't need parallelism

## Quick reference

### When to use which pattern

| Situation | Pattern |
|-----------|---------|
| Need multiple approaches to compare | Branch and Merge |
| Complex deliverable, diverse expertise needed | Multi-Role Team |
| Need thorough critique and polish | Generator-Critic-Editor |
| Large task with natural divisions | Decompose and Farm-Out |

### Pattern selection prompt

```text
For this task: [task]

Which parallel pattern fits best?
1. Branch and Merge — if I need breadth (multiple approaches)
2. Multi-Role Team — if I need diverse perspectives
3. Generator-Critic-Editor — if I need depth (thorough critique)
4. Decompose and Farm-Out — if the task has natural divisions

Recommend one and explain why.
```

---

## Sources

Concepts in this guide are grounded in research and best practices:

- [S0016: Centaur Evaluations](../90_sources/extraction_cards/S0016_centaur_evaluations.md) — human+AI evaluation patterns
- [S0017: The Centaur Programmer](../90_sources/extraction_cards/S0017_centaur_programmer.md) — multi-pass workflows
- [S0005: Self-Consistency Improves CoT](../90_sources/extraction_cards/S0005_self_consistency_cot.md) — sampling multiple paths, merging results

---

## Related

- [Explore → Select → Refine](explore_select_refine.md) — the loop within each thread
- [Which pattern?](../decisions/which_pattern.md) — when to use parallel vs. other patterns
- [Trust Calibration](trust_calibration.md) — verification at merge step
