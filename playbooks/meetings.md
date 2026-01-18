---
title: Meetings Playbook
updated: 2026-01-17
---

# Meetings Playbook

## When to use this

- Processing meeting notes into structured output
- Extracting action items and decisions
- Creating follow-up communications
- Preparing for upcoming meetings

---

## Context template

```text
Role: You are an executive assistant / meeting facilitator.

Task: [Process / Summarize / Prepare for] this meeting.

Inputs:
"""
[Paste meeting notes, transcript, agenda]
"""

Constraints:
- Meeting type: [standup / planning / review / decision / brainstorm]
- Audience for output: [attendees / broader team / leadership]
- Urgency: [need action items now / summary can wait]

Format: [structured summary / email / action list]

Quality bar:
- Action items have owners and dates
- Decisions are captured clearly
- Nothing important is lost
```

---

## Prompt sequence

### 1. Explore: Extract key elements

```text
From these meeting notes:
"""
[paste notes]
"""

Extract:
1. Key decisions made (with who decided)
2. Action items (with owners if mentioned)
3. Open questions / parking lot items
4. Risks or concerns raised
5. Important context mentioned
```

### 2. Select: Prioritize

```text
From these extracted items:

1. Which action items are most urgent?
2. Which decisions need to be communicated broadly?
3. What needs follow-up before next meeting?
4. What can wait?
```

### 3. Refine: Create outputs

```text
Create a meeting summary:

## Summary
[2-3 sentences on what happened]

## Decisions
- [decision 1]
- [decision 2]

## Action Items
| Action | Owner | Due |
|--------|-------|-----|
| [action] | [who] | [when] |

## Open Questions
- [question 1]
- [question 2]

## Next Steps
[what happens next]
```

---

## Verification checklist

Before sending:

- [ ] **Decisions captured**: All decisions explicitly stated
- [ ] **Actions have owners**: Every action has a name attached
- [ ] **Due dates set**: Actions have timeframes
- [ ] **Nothing lost**: Cross-check against original notes
- [ ] **Sensitive content handled**: Nothing inappropriate for audience
- [ ] **Tone appropriate**: Matches meeting culture

---

## Common pitfalls

| Pitfall | Signs | Fix |
|---------|-------|-----|
| Orphan actions | "Someone should..." without owner | Require explicit owner for each action |
| Missed decisions | Decision happened but not captured | Ask "what did we decide about X?" |
| Too verbose | Summary as long as meeting | Focus on decisions and actions |
| Lost context | Summary makes sense today, not next week | Add brief context for each item |
| Wrong audience | Summary includes internal-only info | Specify audience upfront |

---

## Patterns

### Pattern: Meeting notes → Structured summary

Transform raw notes:

```text
Meeting notes:
"""
[paste raw notes / transcript]
"""

Create structured summary:

1. **Meeting**: [title], [date], [attendees]
2. **Purpose**: [one sentence]
3. **Key decisions**: [bulleted list]
4. **Action items**: [table with owner, due date]
5. **Open questions**: [what wasn't resolved]
6. **Next meeting**: [when, purpose]
```

### Pattern: Extract action items

Focus on actions only:

```text
From these notes, extract ALL action items:
"""
[paste notes]
"""

For each action item:
- What: [specific action]
- Who: [owner, or "unassigned" if unclear]
- When: [due date, or "TBD" if unclear]
- Context: [why this matters, one sentence]

Flag any actions without clear owners.
```

### Pattern: Decision log

Capture decisions for the record:

```text
Extract decisions from this meeting:
"""
[paste notes]
"""

For each decision:
- Decision: [what was decided]
- Context: [why this came up]
- Alternatives considered: [what else was discussed]
- Who decided: [decision maker or group]
- Date: [when decided]
```

### Pattern: Follow-up email

Create communication:

```text
Create a follow-up email for this meeting:
"""
[paste notes]
"""

Audience: [attendees / broader team / stakeholders]
Tone: [formal / casual / brief]

Include:
1. Brief summary (2-3 sentences)
2. Key decisions
3. Action items with owners and due dates
4. Next steps
```

### Pattern: Meeting prep

Prepare for an upcoming meeting:

```text
I have a meeting about: [topic]

Attendees: [who will be there]
Goal: [what needs to be accomplished]
Time: [how long]

Help me prepare:
1. Proposed agenda with time allocations
2. Key questions to address
3. Decisions that need to be made
4. Information I should bring
5. Potential challenges and how to handle
```

### Pattern: Standup summary

For recurring standups:

```text
Standup notes:
"""
[paste notes]
"""

Extract per person:
- Yesterday: [what they did]
- Today: [what they'll do]
- Blockers: [what's in the way]

Summary:
- Team blockers (need immediate attention)
- Cross-team dependencies
- Risks to flag
```

---

## Related

- [Writing Playbook](writing.md) — for follow-up communications
- [Analysis Playbook](analysis.md) — for meeting decisions
- [Context Engineering](../concepts/context_engineering.md) — structuring input
