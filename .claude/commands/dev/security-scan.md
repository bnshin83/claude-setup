# Security Scan

Scan code for security vulnerabilities.

## Usage
```
/dev/security-scan [path or file]
```

## OWASP Top 10 Checklist

### 1. Injection
- [ ] SQL injection
- [ ] Command injection
- [ ] LDAP injection
- [ ] XPath injection

### 2. Broken Authentication
- [ ] Weak passwords allowed
- [ ] Missing rate limiting
- [ ] Session fixation
- [ ] Credential exposure in logs

### 3. Sensitive Data Exposure
- [ ] Hardcoded secrets
- [ ] Unencrypted sensitive data
- [ ] Sensitive data in URLs
- [ ] Missing HTTPS

### 4. XML External Entities (XXE)
- [ ] Unsafe XML parsing
- [ ] DTD processing enabled

### 5. Broken Access Control
- [ ] Missing authorization checks
- [ ] IDOR vulnerabilities
- [ ] Directory traversal
- [ ] CORS misconfiguration

### 6. Security Misconfiguration
- [ ] Debug mode in production
- [ ] Default credentials
- [ ] Unnecessary features enabled
- [ ] Missing security headers

### 7. Cross-Site Scripting (XSS)
- [ ] Reflected XSS
- [ ] Stored XSS
- [ ] DOM-based XSS
- [ ] Missing output encoding

### 8. Insecure Deserialization
- [ ] Untrusted data deserialization
- [ ] pickle/marshal usage

### 9. Using Components with Known Vulnerabilities
- [ ] Outdated dependencies
- [ ] Known CVEs

### 10. Insufficient Logging & Monitoring
- [ ] Missing audit logs
- [ ] Sensitive data in logs
- [ ] No alerting

## Quick Scans

```bash
# Find hardcoded secrets
grep -rn "password\|secret\|api_key\|token" --include="*.py" --include="*.js" .

# Find SQL injection risks
grep -rn "execute\|cursor\|query" --include="*.py" .

# Find command injection risks
grep -rn "subprocess\|os.system\|exec\|eval" --include="*.py" .

# Find potential XSS
grep -rn "innerHTML\|dangerouslySetInnerHTML" --include="*.js" --include="*.tsx" .

# Check for debug mode
grep -rn "DEBUG\s*=\s*True\|debug:\s*true" .

# Find TODO security items
grep -rn "TODO.*security\|FIXME.*security\|HACK" .
```

## Output Format
```markdown
## Security Scan: [path]

### Critical 🔴
| Issue | Location | Description |
|-------|----------|-------------|
| SQL Injection | `db.py:45` | User input in query |

### High 🟠
| Issue | Location | Description |
|-------|----------|-------------|
| Hardcoded secret | `config.py:12` | API key in source |

### Medium 🟡
| Issue | Location | Description |
|-------|----------|-------------|
| Missing rate limit | `auth.py:30` | Login endpoint |

### Low 🔵
| Issue | Location | Description |
|-------|----------|-------------|
| Debug logging | `app.py:5` | Verbose in prod |

### Recommendations
1. [Priority fix 1]
2. [Priority fix 2]
```

## Tools Integration

```bash
# Python - bandit
pip install bandit
bandit -r src/

# JavaScript - npm audit
npm audit

# Dependencies - safety
pip install safety
safety check

# Secrets - trufflehog
trufflehog filesystem .
```
