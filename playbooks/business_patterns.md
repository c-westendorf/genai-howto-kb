---
title: Business-Specific Patterns
updated: 2026-01-17
---

# Business-Specific Patterns

Patterns for business work: stakeholder communication, executive summaries, decision memos, competitive analysis.

---

## Stakeholder communication

### Pattern: Audience-adapted messaging

Tailor message to audience:

```text
I need to communicate: [message]

Audiences:
1. [Audience A - e.g., executives]
2. [Audience B - e.g., technical team]
3. [Audience C - e.g., customers]

For each audience, create a version that:
- Uses appropriate level of detail
- Emphasizes what they care about
- Uses their vocabulary
- Has appropriate call-to-action
```

### Pattern: Status update (BLUF)

Bottom Line Up Front for busy stakeholders:

```text
Create a status update for: [project/initiative]

Audience: [who will read this]

Format:
1. **Bottom line** (1 sentence): What they need to know
2. **Status**: On track / At risk / Blocked
3. **Key updates** (3-5 bullets): What happened since last update
4. **Decisions needed**: What you need from them
5. **Next milestones**: What's coming
6. **Risks**: Top concerns (if any)

Keep to one page max.
```

### Pattern: Bad news communication

Deliver difficult messages:

```text
I need to communicate: [bad news - delay, cost overrun, failure, etc.]

Audience: [who needs to know]

Help me structure this:
1. State the situation clearly (no burying the lead)
2. Explain what happened and why
3. Describe the impact
4. Present the plan to address it
5. State what you need from them

Tone: [direct but not defensive, accountable, solution-oriented]
```

---

## Executive summaries

### Pattern: One-pager

Condense for executives:

```text
Create an executive summary for:
"""
[paste longer document]
"""

Constraints:
- One page maximum
- 5th grade reading level for main points
- Executive audience (busy, need bottom line first)

Format:
1. **Key takeaway** (1 sentence)
2. **Context** (2-3 sentences): Why this matters
3. **Findings/recommendations** (3-5 bullets)
4. **Implications** (what this means for us)
5. **Recommended action** (what we should do)
```

### Pattern: Board-ready summary

For board/leadership audiences:

```text
Create a board-ready summary for: [topic]

Content:
"""
[paste source material]
"""

This audience cares about:
- Strategic implications
- Financial impact
- Risks and mitigations
- Competitive position
- Timeline and milestones

Format: 3-5 slides worth of content, with talking points for each.
```

---

## Decision memos

### Pattern: Decision memo structure

Document a decision for the record:

```text
Create a decision memo:

## Decision
[One sentence: what we're deciding]

## Context
[Why this decision is needed now - 2-3 sentences]

## Options considered
| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| A | [brief] | [list] | [list] |
| B | [brief] | [list] | [list] |
| C | [brief] | [list] | [list] |

## Recommendation
[Which option and why - tied to decision criteria]

## Trade-offs
[What we're giving up by choosing this]

## Risks and mitigations
| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| [risk] | H/M/L | H/M/L | [how we'll address] |

## Next steps
| Action | Owner | Due |
|--------|-------|-----|
| [action] | [who] | [when] |
```

### Pattern: Recommendation with options

Present options fairly while recommending:

```text
Topic: [what we're deciding]

Create a recommendation:
1. Frame the decision (what we're choosing between, why now)
2. Present 3 options fairly (not straw-man alternatives)
3. State decision criteria (what matters most)
4. Make a clear recommendation
5. Explain why it's better than alternatives
6. Acknowledge trade-offs
7. Define success criteria (how we'll know it worked)
```

---

## Competitive analysis

### Pattern: Competitive landscape

Map the competitive space:

```text
Create a competitive analysis for: [our product/market]

Known competitors: [list if known]

Analyze:
1. **Market map**: Who competes where
2. **Positioning**: How each competitor positions
3. **Strengths/weaknesses**: By competitor
4. **Our differentiation**: Where we win
5. **Threats**: Where competitors are gaining
6. **Opportunities**: Gaps in the market

Note: Flag any claims that need verification with [VERIFY].
```

### Pattern: Competitor deep dive

Analyze a specific competitor:

```text
Analyze competitor: [name]

Areas to cover:
1. **Product**: What they offer, key features
2. **Positioning**: How they message, who they target
3. **Pricing**: Model, price points (if known)
4. **Strengths**: Where they're better than us
5. **Weaknesses**: Where we have advantage
6. **Strategy**: What they seem to be focused on
7. **Implications**: What we should do about this

Sources to cite: [any provided context]
Flag speculation as [UNVERIFIED].
```

---

## PRD and requirements

### Pattern: PRD section

Draft a PRD section:

```text
Write a PRD section for: [feature]

Context:
"""
[paste any requirements, user research, constraints]
"""

Include:
1. **Problem statement**: What user problem we're solving
2. **User stories**: As a [user], I want [goal], so that [benefit]
3. **Requirements**: Must have / Should have / Nice to have
4. **Success metrics**: How we'll measure success
5. **Non-goals**: What we're explicitly NOT doing
6. **Dependencies**: What this requires
7. **Open questions**: What we still need to figure out
```

### Pattern: Requirements clarification

Fill gaps in requirements:

```text
Here are the requirements I've been given:
"""
[paste requirements]
"""

Help me clarify:
1. What's ambiguous or underspecified?
2. What questions should I ask the requester?
3. What edge cases aren't covered?
4. What assumptions am I making?
5. What might conflict with other requirements?
```

---

## Common business pitfalls

| Pitfall | Signs | Fix |
|---------|-------|-----|
| Burying the lead | Key point on page 3 | BLUF pattern - bottom line first |
| Too much detail | Executives lost in weeds | Layer information - summary then details |
| Vague recommendations | "We should consider..." | Make specific recommendation with rationale |
| No ask | Stakeholder doesn't know what you need | Clear call to action |
| Unverified claims | Competitive "analysis" from model knowledge | Flag as [VERIFY], use provided sources |

---

## Verification for business work

- [ ] **Audience-appropriate**: Right level of detail and vocabulary
- [ ] **Bottom line clear**: Reader knows key point immediately
- [ ] **Claims sourced**: Factual claims have sources or are flagged
- [ ] **Ask clear**: Reader knows what you need from them
- [ ] **Actionable**: Next steps are specific and owned

---

## Related

- [Writing Playbook](writing.md) — general writing patterns
- [Analysis Playbook](analysis.md) — decision analysis
- [Research Playbook](research.md) — competitive research
- [Trust Calibration](../concepts/trust_calibration.md) — verification for business docs
