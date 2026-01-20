---
title: Playbooks
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](index.md) · [Reference](../reference/index.md)

# Playbooks

Grab-and-go guides for common tasks. Each includes context template, prompt patterns, verification checklist, and common pitfalls.

---

## By task type

### [Writing & Drafting](writing.md)
PRDs, docs, emails, reports, summaries. When you need to produce written artifacts.

### [Analysis & Decisions](analysis.md)
Options comparison, recommendations, pre-mortems, decision memos. When you need to evaluate and choose.

### [Research & Synthesis](research.md)
Finding sources, extracting insights, synthesizing across materials. When you need to understand something.

### [Code & Technical](code.md)
Code review, debugging, documentation, test generation. When you're working with code.

### [Meetings](meetings.md)
Notes, action items, follow-ups, summaries. When you need to capture and process meeting content.

---

## By role

What's different for your context:

### [DS-Specific Patterns](ds_patterns.md)
Experiment design, statistical analysis, model interpretation, data quality assessment. Patterns for data science work.

### [MLE-Specific Patterns](mle_patterns.md)
Spec-first coding, test generation, security review, documentation. Patterns for ML engineering work.

### [GSD+RALPH Method](mle_gsd_ralph.md)
Complete workflow for AI-assisted development: GSD for genAI-friendly task specs (using `...` expansion markers), RALPH for context-clean execution loops. For complex implementations spanning multiple sessions.

### [Business-Specific Patterns](business_patterns.md)
Stakeholder comms, executive summaries, decision memos, competitive analysis. Patterns for business work.

### [AI Coding Environment Patterns](ide_environment.md)
Configuring AI coding assistants (Claude Code, Cursor, etc.) for effective work: context window hygiene, reusable skills, automated hooks, parallel execution implementation, and subagent delegation. Level 4 content for power users.

---

## How to use playbooks

1. **Find the right playbook** — by task type or role
2. **Copy the context template** — fill in your specifics
3. **Follow the prompt sequence** — explore, select, refine
4. **Run the verification checklist** — before considering it done
5. **Watch for common pitfalls** — each playbook lists what goes wrong

Playbooks are starting points, not scripts. Adapt them to your context.

---

## Quick context template (universal)

```
Role: [who the model should be]
Task: [what you want done]
Inputs: [what you're providing]
Constraints: [boundaries and requirements]
Format: [output structure]
Quality bar: [what "good" looks like]
```

See [Context Pack Template](../reference/templates/context_pack.md) for the full version.
