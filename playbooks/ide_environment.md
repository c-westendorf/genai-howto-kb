---
title: AI Coding Environment Patterns
updated: 2026-01-20
source_attribution: "Patterns derived from community best practices, including @affaanmustafa's Claude Code workflow guide"
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Writing](writing.md) · [Analysis](analysis.md) · [Research](research.md) · [Code](code.md) · [Meetings](meetings.md) · [DS Patterns](ds_patterns.md) · [MLE Patterns](mle_patterns.md) · [GSD+RALPH](mle_gsd_ralph.md) · [Business](business_patterns.md) · [IDE Environment](ide_environment.md)

# AI Coding Environment Patterns

Patterns for configuring AI coding assistants (Claude Code, Cursor, Windsurf, etc.) to work effectively with the concepts in this guide.

This is **Level 4** content — for users who are already comfortable with [context engineering](../concepts/context_engineering.md) and [parallel execution](../concepts/parallel_execution.md) and want to operationalize these concepts in their tools.

---

## Why environment configuration matters

Your AI coding assistant's effectiveness depends on how it's configured:

| Configuration | Impact |
|---------------|--------|
| Too many tools enabled | Context window consumed by tool definitions, not your code |
| No reusable prompts | Repeating the same setup every session |
| No automation | Manual steps that should be automatic |
| Single-threaded work | Missing parallelism opportunities |

The concepts in this guide describe *what* to do. This playbook describes *where* to configure it.

---

## Core patterns

### 1. Context window hygiene

**The problem**: AI coding assistants load tool definitions into context. Each MCP server, plugin, or extension consumes context window space — often before you've typed anything.

**The pattern**: Enable only what you need, per project.

**Tactics**:
- **Audit your tool count**: Many assistants show active tool count. Keep it under 80 active tools.
- **Disable at project level**: Configure unused tools as disabled per-project, not globally
- **Batch by workflow**: Enable database tools for backend work, disable for frontend
- **Watch for symptoms**: If outputs degrade, check if tool bloat is the cause

**Why this matters**: A 200k context window might effectively be 70k with too many tools enabled. Performance degrades before you notice.

See [Context Bloat](../pitfalls/context_bloat.md) for the underlying concept.

---

### 2. Reusable prompt shortcuts (Skills/Commands)

**The problem**: You're writing the same setup prompts repeatedly — "use TDD", "follow our coding standards", "run through these checks".

**The pattern**: Save reusable prompts as skills or commands.

**What these are**: Named prompt shortcuts that inject context, instructions, or workflows. Different tools call them different things:
- Claude Code: Skills (`~/.claude/skills/`) and Commands (`~/.claude/commands/`)
- Cursor: Rules (`.cursor/rules`)
- Generic: Saved prompts, snippets, templates

**Good candidates for skills**:
- Testing workflows: `/tdd`, `/test-coverage`, `/e2e`
- Code quality: `/refactor-clean`, `/security-review`
- Project-specific patterns: `/our-api-style`, `/db-conventions`
- Chained workflows: Skills can call other skills

**How this connects to context engineering**: A skill is a reusable [context pack](../concepts/context_engineering.md) — role, task, constraints, format bundled for repeated use.

---

### 3. Automated quality gates (Hooks)

**The problem**: You want certain checks to run automatically — formatting, linting, reminders — without manually prompting each time.

**The pattern**: Configure hooks that trigger on specific events.

**Hook types** (terminology varies by tool):
- **Pre-execution**: Before a tool runs (validation, reminders)
- **Post-execution**: After a tool finishes (formatting, feedback)
- **On prompt submit**: When you send a message
- **On completion**: When the assistant finishes responding

**Good candidates for hooks**:
- Auto-format code after edits (Prettier, Black, etc.)
- Run type-check after TypeScript edits
- Warn about console.log statements
- Remind about tmux for long-running commands
- Block creation of unnecessary files

**The principle**: Automate the repetitive verification steps you'd otherwise forget or skip.

---

### 4. Parallel execution implementation

**The problem**: You understand [parallel execution](../concepts/parallel_execution.md) conceptually but need to implement it in your tools.

**Pattern A: Conversation forking**

Most AI coding assistants support forking a conversation into independent branches:
- Use for non-overlapping tasks
- Each fork maintains its own context
- Merge results manually when done

**Pattern B: Git worktrees for overlapping work**

When you need multiple AI sessions working on the same codebase:

```bash
git worktree add ../feature-branch feature-branch
# Run separate AI assistant instances in each worktree
```

Each worktree is an independent checkout — no file conflicts between sessions.

**Pattern C: Session persistence (tmux)**

For long-running commands the AI executes:

```bash
tmux new -s dev
# AI runs commands here
# You can detach (Ctrl+B, D) and reattach later
tmux attach -t dev
```

Lets you monitor logs and processes the AI spins up.

---

### 5. Delegation patterns (Subagents)

**The problem**: Your main conversation is accumulating context from diverse tasks — planning, coding, reviewing, testing.

**The pattern**: Delegate specific tasks to scoped subagents.

**What subagents are**: Processes your main conversation can spawn with limited scope. They:
- Have their own context (don't pollute the main thread)
- Can be restricted to specific tools
- Run in background or foreground
- Return results to the main thread

**Example subagent roles**:
- **Planner**: Feature breakdown, implementation planning
- **Architect**: System design decisions
- **Reviewer**: Code quality, security review
- **Test runner**: Execute and report on tests
- **Refactor cleaner**: Dead code removal, cleanup

**The principle**: Match subagent scope to task scope. A security reviewer doesn't need write access. A test runner doesn't need to edit production code.

This is the "Decompose and Farm-Out" pattern from [Parallel Execution](../concepts/parallel_execution.md), implemented at the tool level.

---

### 6. External service connections (MCPs)

**The problem**: You're copy-pasting between your database, deployment platform, documentation, and the AI assistant.

**The pattern**: Connect services directly via Model Context Protocol (MCP) or equivalent.

**What MCPs enable**:
- Query databases directly from conversation
- Pull deployment status without leaving context
- Access live documentation
- Interact with external APIs

**The tradeoff**: Each MCP connection adds tools to your context window. Connect only what you need for the current project.

**Good candidates for MCP connections**:
- Database (query, but not write in production)
- Version control (GitHub PRs, issues)
- Documentation sources
- Deployment platforms (status, logs)

**Avoid over-connecting**: Having 20 MCPs configured but only 5 enabled is better than having all 20 active.

---

### 7. Project-level configuration

**The problem**: Global settings don't match project-specific needs.

**The pattern**: Layer configuration at user, project, and session levels.

**Configuration hierarchy** (typical):
1. **User level**: Your defaults across all projects
2. **Project level**: Overrides for specific codebases (`.claude/`, `.cursor/`, etc.)
3. **Session level**: Temporary overrides for current work

**What to configure at project level**:
- Disabled tools (MCPs, plugins not needed for this project)
- Project-specific skills and commands
- Rules and conventions unique to this codebase
- Context files (see [GSD+RALPH](mle_gsd_ralph.md) for CLAUDE.md patterns)

**Example project rules**:
- "No emojis in code comments"
- "Always use our internal date library, not moment.js"
- "Follow the existing error handling pattern in /src/errors"
- "Never commit console.log statements"

---

## How these connect to core concepts

| Environment Pattern | Core Concept | Link |
|---------------------|--------------|------|
| Context window hygiene | Context Engineering, Context Bloat | [Context Engineering](../concepts/context_engineering.md), [Context Bloat](../pitfalls/context_bloat.md) |
| Skills/Commands | Context Packs (reusable) | [Context Engineering](../concepts/context_engineering.md) |
| Hooks | Automation, verification | [Trust Calibration](../concepts/trust_calibration.md) |
| Conversation forking | Branch and Merge | [Parallel Execution](../concepts/parallel_execution.md) |
| Subagents | Decompose and Farm-Out | [Parallel Execution](../concepts/parallel_execution.md) |
| Project config | Context Engineering | [Context Engineering](../concepts/context_engineering.md) |

---

## Quick setup checklist

- [ ] Audit active tool count — aim for under 80
- [ ] Disable unused MCPs/plugins at project level
- [ ] Create skills for your top 3 repetitive workflows
- [ ] Set up at least one quality-gate hook (formatting or linting)
- [ ] Configure project-level rules for current codebase
- [ ] Know how to fork conversations in your tool
- [ ] Set up git worktrees if you need parallel AI sessions

---

## Tool-specific documentation

Configuration specifics vary by tool. Consult your tool's docs for syntax:

- **Claude Code**: [docs.anthropic.com/claude-code](https://docs.anthropic.com/claude-code)
- **Cursor**: [cursor.sh/docs](https://cursor.sh/docs)
- **Windsurf**: Consult Windsurf documentation
- **Aider**: [aider.chat](https://aider.chat)

---

## Related

- [Context Engineering](../concepts/context_engineering.md) — the underlying principle
- [Parallel Execution](../concepts/parallel_execution.md) — conceptual patterns for parallel work
- [Context Bloat](../pitfalls/context_bloat.md) — when context window management fails
- [GSD+RALPH Method](mle_gsd_ralph.md) — project context files and execution loops
