---
title: Code & Technical Playbook
updated: 2026-01-17
---

> **Navigation**: [START HERE](../START_HERE.md) · [Concepts](../concepts/index.md) · [Pitfalls](../pitfalls/index.md) · [Decisions](../decisions/index.md) · [Playbooks](index.md) · [Reference](../reference/index.md)
>
> **In this section**: [Writing](writing.md) · [Analysis](analysis.md) · [Research](research.md) · [Code](code.md) · [Meetings](meetings.md) · [DS Patterns](ds_patterns.md) · [MLE Patterns](mle_patterns.md) · [GSD+RALPH](mle_gsd_ralph.md) · [Business](business_patterns.md)

# Code & Technical Playbook

## When to use this

- Code review and improvement
- Debugging and troubleshooting
- Documentation generation
- Test generation
- Technical design exploration

---

## Context template

```text
Role: You are a senior [language/framework] developer.

Task: [Review / Debug / Document / Test / Design] this code.

Inputs:
"""
[Paste code, error messages, requirements]
"""

Constraints:
- Language/framework: [specify]
- Style guide: [if applicable]
- Performance requirements: [if applicable]
- Security considerations: [if applicable]

Format: [code blocks with explanations / diff format / step-by-step]

Quality bar:
- Code is correct and handles edge cases
- Changes are minimal and focused
- Reasoning is explained
```

---

## Prompt sequence

### 1. Explore: Understand before changing

```text
Before making changes, analyze this code:

1. What does it do? (one paragraph)
2. What are the inputs and outputs?
3. What are the edge cases?
4. What could go wrong?
5. What's unclear or concerning?
```

### 2. Select: Choose approach

```text
For this improvement: [what you want to change]

Give me 3 approaches:
1. Minimal fix (smallest change that works)
2. Refactored solution (cleaner but more change)
3. Robust solution (handles edge cases, future-proof)

Trade-offs for each. Recommend one.
```

### 3. Refine: Implement and verify

```text
Implement approach [X].

Show:
1. The code change (with before/after or diff)
2. Why this works
3. Edge cases it handles
4. How to test it
```

---

## Verification checklist

Before using generated code:

- [ ] **Read it**: Understand what it does
- [ ] **Test it**: Run with normal and edge cases
- [ ] **Check edge cases**: Empty input, null, boundaries
- [ ] **Security review**: No injection, proper validation
- [ ] **Error handling**: Fails gracefully
- [ ] **Matches context**: Works with surrounding code

---

## Common pitfalls

| Pitfall | Signs | Fix |
|---------|-------|-----|
| Works in isolation, fails in context | Doesn't integrate | Provide surrounding code context |
| Missing edge cases | Fails on empty/null/boundary | Explicitly ask for edge case handling |
| Insecure code | Injection, hardcoded secrets | Ask for security review |
| Over-engineered | Simple problem, complex solution | Ask for minimal solution first |
| Outdated patterns | Uses deprecated APIs | Specify version, ask for current best practice |

---

## Patterns

### Pattern: Spec-first development

Define before implementing:

```text
I need to implement: [feature]

First, create a spec:
1. Function signature (inputs, outputs, types)
2. Behavior for normal cases
3. Behavior for edge cases (empty, null, invalid)
4. Error handling approach
5. Example usage

Don't write code yet. Just the spec.
```

Then:
```text
Now implement according to this spec.
Include tests that verify each behavior.
```

### Pattern: Code review

Systematic review:

```text
Review this code:
"""
[paste code]
"""

Check for:
1. Correctness: Does it do what it's supposed to?
2. Edge cases: What inputs would break it?
3. Security: Any vulnerabilities? (injection, validation, secrets)
4. Performance: Any obvious inefficiencies?
5. Readability: Is it clear? Good names? Comments where needed?

List issues by severity (critical/medium/low).
```

### Pattern: Debugging

Systematic diagnosis:

```text
This code produces: [unexpected behavior]
Expected: [what should happen]

Code:
"""
[paste code]
"""

Error (if any):
"""
[paste error]
"""

Debug:
1. What's the likely cause?
2. How would you verify?
3. What's the fix?
4. How to prevent this in future?
```

### Pattern: Test generation

Generate tests from code:

```text
Generate tests for this function:
"""
[paste function]
"""

Include:
1. Happy path tests
2. Edge cases (empty, null, boundary values)
3. Error cases (invalid inputs)
4. Use [testing framework] syntax
```

### Pattern: Documentation generation

Generate docs from code:

```text
Document this code:
"""
[paste code]
"""

Generate:
1. One-line summary
2. Parameters (name, type, description)
3. Return value
4. Exceptions/errors
5. Usage example
6. Edge case notes

Use [docstring format].
```

### Pattern: Explain code

Understand unfamiliar code:

```text
Explain this code:
"""
[paste code]
"""

1. What does it do? (one paragraph)
2. Walk through it step by step
3. What are the key decisions/patterns used?
4. What could be confusing to a new reader?
5. Any potential issues or improvements?
```

---

## Security checklist

For any code that will run:

- [ ] **Input validation**: All inputs checked
- [ ] **No injection**: SQL, command, script injection prevented
- [ ] **No hardcoded secrets**: Credentials externalized
- [ ] **Error messages**: Don't leak sensitive info
- [ ] **Dependencies**: No known vulnerabilities
- [ ] **Permissions**: Least privilege

---

## Related

- [Context Engineering](../concepts/context_engineering.md) — structuring code context
- [Trust Calibration](../concepts/trust_calibration.md) — verification for code
- [MLE-specific patterns](mle_patterns.md) — ML engineering patterns
