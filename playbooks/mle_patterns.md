---
title: MLE-Specific Patterns
updated: 2026-01-17
---

# MLE-Specific Patterns

Patterns for ML engineering work: spec-first development, test generation, security review, system design.

---

## Spec-first development

### Pattern: Define before implementing

Don't start coding. Start with a spec:

```text
I need to implement: [feature/function]

Create a specification first:

1. **Interface**
   - Function signature (inputs, outputs, types)
   - Class structure (if applicable)

2. **Behavior**
   - Normal case: what should happen
   - Edge cases: empty, null, boundary, invalid
   - Error handling: what errors, how handled

3. **Examples**
   - 3 usage examples with expected output

4. **Constraints**
   - Performance requirements
   - Security considerations
   - Compatibility requirements

Don't write code yet. Just the spec.
```

Then implement:
```text
Now implement according to this spec.
After the implementation, show how each spec requirement is satisfied.
```

### Pattern: API design

Design APIs before implementing:

```text
I need an API for: [purpose]

Consumers: [who will use this]

Design the API:
1. Endpoints / function signatures
2. Request/response schemas
3. Error responses
4. Authentication/authorization approach
5. Rate limiting / quotas
6. Example requests and responses

Consider:
- Backward compatibility
- Versioning strategy
- Common use cases
```

---

## Test generation

### Pattern: Test-first from spec

Generate tests before code:

```text
Given this spec:
"""
[paste spec]
"""

Generate tests BEFORE the implementation:

1. Unit tests for each behavior in spec
2. Edge case tests
3. Error handling tests
4. Integration tests (if applicable)

Use [testing framework] syntax.
Don't write the implementation yet.
```

### Pattern: Test suite for existing code

Add tests to existing code:

```text
Generate comprehensive tests for:
"""
[paste code]
"""

Include:
1. Happy path tests
2. Edge cases:
   - Empty/null inputs
   - Boundary values
   - Invalid inputs
3. Error cases
4. State tests (if stateful)
5. Performance tests (if applicable)

For each test, explain what it's testing and why.
```

### Pattern: Property-based testing

Generate property tests:

```text
For this function:
"""
[paste function]
"""

What properties should always hold?
1. Invariants (what's always true)
2. Relationships (input-output relationships)
3. Roundtrip properties (encode-decode, save-load)
4. Commutativity/associativity (if applicable)

Generate property-based tests using [framework].
```

---

## Security review

### Pattern: Security-focused code review

Review for security:

```text
Security review this code:
"""
[paste code]
"""

Check for:
1. **Injection**: SQL, command, script injection points
2. **Validation**: Input validation, output encoding
3. **Authentication/Authorization**: Proper checks
4. **Secrets**: Hardcoded credentials, exposed secrets
5. **Logging**: Sensitive data in logs
6. **Dependencies**: Known vulnerable libraries
7. **Error handling**: Information leakage in errors

For each finding:
- Severity: critical/high/medium/low
- Location: where in the code
- Risk: what could happen
- Fix: how to remediate
```

### Pattern: Threat modeling

For system design:

```text
Threat model this system:
"""
[paste architecture/design]
"""

Analyze:
1. **Assets**: What are we protecting?
2. **Threats**: Who might attack? How?
3. **Attack surfaces**: Where are entry points?
4. **Trust boundaries**: Where does trust change?
5. **Vulnerabilities**: Where are we weak?
6. **Mitigations**: How to address each threat

Use STRIDE or similar framework.
```

### Pattern: Prompt injection review

For LLM-integrated code:

```text
Review this LLM integration for prompt injection:
"""
[paste code]
"""

Check:
1. How is user input incorporated into prompts?
2. Is there untrusted content (web, email, docs)?
3. Are outputs constrained to a schema?
4. Is output validated before use?
5. Can the LLM take actions? What actions?
6. Are actions properly scoped and authorized?

For each risk: severity, attack scenario, mitigation.
```

---

## System design

### Pattern: Design exploration

Explore options before committing:

```text
I need to build: [system/feature]

Requirements:
- [functional requirements]
- [non-functional: scale, latency, reliability]

Explore 3 architectural approaches:
1. [simple but might not scale]
2. [robust but complex]
3. [something different]

For each:
- High-level architecture
- Key components
- Trade-offs
- When it would fail
```

### Pattern: Design review

Review a design:

```text
Review this design:
"""
[paste design doc or diagram]
"""

Evaluate:
1. Does it meet the requirements?
2. Scalability: What breaks at 10x, 100x?
3. Reliability: Single points of failure?
4. Security: What's the attack surface?
5. Operability: How do we monitor, debug, deploy?
6. Cost: What are the cost drivers?

What questions would you ask in a design review?
```

---

## ML-specific patterns

### Pattern: ML pipeline review

Review ML system:

```text
Review this ML pipeline:
"""
[paste pipeline description/code]
"""

Check:
1. **Data quality**: How is data validated?
2. **Feature engineering**: Reproducible? Documented?
3. **Training**: Reproducible? Versioned?
4. **Evaluation**: Right metrics? Holdout strategy?
5. **Serving**: Latency? Fallbacks?
6. **Monitoring**: Drift detection? Performance tracking?
7. **Retraining**: When? How triggered?
```

### Pattern: Model deployment checklist

Before deploying:

```text
Pre-deployment review for model: [model name]

1. **Performance validated**: Metrics on holdout/production-like data
2. **Fairness checked**: Performance across subgroups
3. **Latency verified**: Meets SLA requirements
4. **Fallback defined**: What happens if model fails
5. **Monitoring ready**: Dashboards, alerts configured
6. **Rollback plan**: How to revert if issues
7. **Documentation complete**: Model card, runbook
8. **Stakeholder approval**: Sign-off from owners
```

---

## Extended MLE workflows

For complete methodologies beyond individual patterns:

- [GSD+RALPH Method](mle_gsd_ralph.md) — GSD for genAI-friendly task specs + RALPH for context-clean execution loops. Use for complex implementations spanning multiple sessions.

---

## Common MLE pitfalls

| Pitfall | Signs | Fix |
|---------|-------|-----|
| No spec | Coding without clear requirements | Spec-first pattern |
| Missing tests | "Works on my machine" | Test-first pattern |
| Security afterthought | No threat modeling | Security review early |
| Over-engineering | Complex for simple problem | Start simple, add complexity when proven needed |
| Unclear rollback | "Just deploy and see" | Define rollback before deploy |

---

## Verification for MLE work

- [ ] **Spec satisfied**: Implementation matches spec
- [ ] **Tests pass**: Unit, integration, edge cases
- [ ] **Security reviewed**: No obvious vulnerabilities
- [ ] **Documented**: Someone else can understand and maintain
- [ ] **Deployable**: Can be deployed and rolled back safely
- [ ] **Observable**: Can monitor in production

---

## Related

- [Code Playbook](code.md) — general code patterns
- [Trust Calibration](../concepts/trust_calibration.md) — verification for code
- [Parallel Execution](../concepts/parallel_execution.md) — spec-first + test-first as parallel pattern
