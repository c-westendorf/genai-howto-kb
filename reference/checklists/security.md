---
title: Security Checklist
updated: 2026-01-17
---

# Security Checklist

Security checks for genAI-generated code and content. Use before deploying or sharing.

---

## Code security checklist

### Input validation

- [ ] **All inputs validated**: User input, API parameters, file contents checked
- [ ] **Type checking**: Inputs are expected types
- [ ] **Length limits**: String lengths and array sizes bounded
- [ ] **Range checking**: Numeric values within expected ranges
- [ ] **Format validation**: Emails, URLs, dates validated for format
- [ ] **Sanitization**: Dangerous characters escaped or removed

### Injection prevention

- [ ] **SQL injection**: Parameterized queries, no string concatenation
- [ ] **Command injection**: No shell commands with user input, proper escaping
- [ ] **Script injection (XSS)**: Output encoding, Content-Security-Policy
- [ ] **Path traversal**: No user input in file paths, or properly sanitized
- [ ] **Template injection**: User input not interpreted as template code
- [ ] **LDAP/XML/other injection**: Protocol-specific sanitization applied

### Authentication & Authorization

- [ ] **Auth required**: Protected endpoints require authentication
- [ ] **Auth verified**: Tokens/sessions validated server-side
- [ ] **Authorization checked**: User has permission for requested action
- [ ] **Least privilege**: Code runs with minimum necessary permissions
- [ ] **Session management**: Secure session handling, timeout, invalidation

### Secrets management

- [ ] **No hardcoded secrets**: API keys, passwords, tokens not in code
- [ ] **Environment variables**: Secrets loaded from secure source
- [ ] **Secrets not logged**: Sensitive data not written to logs
- [ ] **Secrets not in URLs**: No tokens in query strings
- [ ] **Secrets not in responses**: Error messages don't expose secrets

### Error handling

- [ ] **Graceful failures**: Errors don't crash the system
- [ ] **No stack traces**: Error messages don't expose internals
- [ ] **No sensitive data in errors**: Errors don't leak user data or secrets
- [ ] **Appropriate logging**: Errors logged for debugging, not exposed to users
- [ ] **Fail secure**: Failures default to deny, not allow

### Dependencies

- [ ] **Known vulnerabilities checked**: Dependencies scanned for CVEs
- [ ] **Minimal dependencies**: Only necessary packages included
- [ ] **Pinned versions**: Dependencies locked to specific versions
- [ ] **Trusted sources**: Packages from official repositories
- [ ] **License compliance**: Dependencies have compatible licenses

### Data protection

- [ ] **Encryption in transit**: HTTPS, TLS for all connections
- [ ] **Encryption at rest**: Sensitive data encrypted when stored
- [ ] **PII handling**: Personal data minimized, protected, logged appropriately
- [ ] **Data sanitization**: Sensitive data removed from logs, responses
- [ ] **Retention limits**: Data not kept longer than necessary

---

## Content security checklist

### For external-facing content

- [ ] **No internal information**: No internal URLs, employee names, project codes
- [ ] **No sensitive data**: No customer data, credentials, financial info
- [ ] **No private communications**: No internal emails, Slack, meeting notes
- [ ] **No proprietary information**: No trade secrets, unreleased products
- [ ] **Appropriate disclaimers**: AI-generated content disclosed if required

### For LLM-integrated systems

- [ ] **Prompt injection resistance**: User input can't hijack the prompt
- [ ] **Output validation**: LLM output validated before use
- [ ] **Action scope limits**: LLM can only trigger allowed actions
- [ ] **Rate limiting**: Abuse prevention on LLM endpoints
- [ ] **Content filtering**: Harmful outputs detected and blocked
- [ ] **Audit logging**: LLM inputs and outputs logged for review

---

## Quick security review prompts

### Initial security scan

```text
Security review this code:
"""
[paste code]
"""

Check for:
1. Injection vulnerabilities (SQL, command, XSS)
2. Authentication/authorization issues
3. Hardcoded secrets or credentials
4. Input validation gaps
5. Error handling that leaks information
6. Insecure dependencies

For each finding: severity (critical/high/medium/low), location, risk, fix.
```

### Focused injection check

```text
Review this code specifically for injection vulnerabilities:
"""
[paste code]
"""

For each user input:
1. Where does it come from?
2. How is it used?
3. Is it properly sanitized/escaped?
4. Could an attacker craft input to break out of intended context?
```

### Secrets audit

```text
Check this code for secrets exposure:
"""
[paste code]
"""

Look for:
1. Hardcoded credentials, API keys, tokens
2. Secrets in URLs or query strings
3. Secrets logged or exposed in errors
4. Insecure secret storage
```

### LLM integration security

```text
Review this LLM integration for security:
"""
[paste code]
"""

Check:
1. Can user input manipulate the prompt?
2. Is LLM output validated before use?
3. What actions can the LLM trigger?
4. Is there rate limiting?
5. Is there content filtering?
6. What happens if the LLM returns unexpected output?
```

---

## OWASP Top 10 quick reference

| Vulnerability | What to check |
|---------------|---------------|
| Injection | Parameterized queries, input sanitization |
| Broken Authentication | Strong passwords, session management, MFA |
| Sensitive Data Exposure | Encryption, minimal data retention |
| XML External Entities | Disable DTDs, use safe parsers |
| Broken Access Control | Authorization on every request, least privilege |
| Security Misconfiguration | Default credentials, unnecessary features disabled |
| Cross-Site Scripting | Output encoding, CSP headers |
| Insecure Deserialization | Don't deserialize untrusted data |
| Known Vulnerabilities | Dependency scanning, patching |
| Insufficient Logging | Log security events, monitor for anomalies |

---

## When to get expert review

Always escalate to security experts when:

- [ ] Handling authentication/authorization logic
- [ ] Processing payments or financial transactions
- [ ] Storing or transmitting PII or health data
- [ ] Building crypto or security primitives
- [ ] Creating public-facing APIs
- [ ] Integrating with external systems
- [ ] Unsure about any security aspect

---

## Red flags in AI-generated code

Watch for these common issues in genAI code:

| Red flag | Why it matters | What to do |
|----------|----------------|------------|
| String concatenation in queries | SQL injection | Use parameterized queries |
| `eval()` or `exec()` with user input | Code injection | Never use with untrusted input |
| Shell commands with variables | Command injection | Use libraries, not shell commands |
| Hardcoded localhost/passwords | Works locally, breaks in prod | Use environment variables |
| Catch-all error handlers | May swallow security errors | Handle errors specifically |
| `dangerouslySetInnerHTML` | XSS in React | Sanitize or avoid |
| Disabled SSL verification | MITM attacks | Always verify SSL |
| `chmod 777` or wide permissions | Access control bypass | Use minimal permissions |

---

## Related

- [Code Playbook](../../playbooks/code.md) — code review patterns
- [MLE Patterns](../../playbooks/mle_patterns.md) — security review for ML systems
- [Trust Calibration](../../concepts/trust_calibration.md) — matching verification to risk
