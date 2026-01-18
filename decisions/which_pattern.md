---
title: What Pattern Should I Use?
updated: 2026-01-17
---

# What Pattern Should I Use?

## Quick answer

- **Simple, low-stakes, well-defined** → Single-shot
- **Complex, needs exploration** → Thought partnership (explore/select/refine)
- **Very complex, needs breadth** → Parallel execution

## Decision criteria

### Use Single-Shot when:

- Task is well-defined and constrained
- You know exactly what you want
- Output is a transformation, not a creation (summarize, extract, reformat)
- Stakes are low — first draft is good enough to iterate on your own
- Time is critical — you need something fast

**Examples:**
- Summarize this document in 3 bullets
- Convert this data to JSON
- Proofread this email
- Extract action items from meeting notes

### Use Thought Partnership when:

- Task requires exploring options
- You're not sure what the right approach is
- Output is a creation, not just transformation
- Stakes are medium — quality matters
- You want to make explicit decisions, not accept defaults

**Examples:**
- Design an experiment plan
- Write a PRD section
- Structure a presentation
- Analyze trade-offs for a decision

### Use Parallel Execution when:

- Task needs multiple perspectives
- You want breadth, not just depth
- Different roles/approaches might give different answers
- Stakes are high — you need to triangulate
- You can merge multiple outputs

**Examples:**
- Generate multiple solution approaches and compare
- Have "generator," "critic," and "editor" roles
- Break a task into independent subtasks
- Get multiple stakeholder perspectives simulated

## Decision tree

```
Is the task well-defined with a clear output format?
├── YES: Do you know exactly what you want?
│   ├── YES → Single-shot
│   └── NO → Thought partnership (explore first)
└── NO: Do you need multiple perspectives or approaches?
    ├── YES → Parallel execution
    └── NO → Thought partnership (explore to define it)
```

## Patterns overview

| Pattern | When | How | Cost |
|---------|------|-----|------|
| **Single-shot** | Known, constrained | One prompt, one output | Low |
| **Thought partnership** | Unknown, needs exploration | Explore → select → refine | Medium |
| **Parallel execution** | Complex, needs breadth | Multiple threads → merge | High |

## Examples by task type

| Task | Pattern | Why |
|------|---------|-----|
| Summarize a document | Single-shot | Well-defined transformation |
| Write a project brief | Thought partnership | Needs exploration of approaches |
| Design system architecture | Parallel execution | Needs multiple perspectives |
| Extract data to table | Single-shot | Clear format, no ambiguity |
| Create experiment plan | Thought partnership | Needs trade-off exploration |
| Review code for bugs | Parallel execution | Different reviewers catch different things |

---

## Related

- [Explore → Select → Refine](../concepts/explore_select_refine.md) — how to run thought partnership
- [Parallel Execution](../concepts/parallel_execution.md) — how to run multiple threads
- [How much verification?](how_much_verification.md) — complements pattern choice
