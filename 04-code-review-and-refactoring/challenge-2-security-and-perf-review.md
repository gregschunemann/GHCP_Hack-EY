# Challenge: Security & Performance Review

| | |
|---|---|
| **Track** | Code Review & Refactoring |
| **Difficulty** | ⭐⭐ Intermediate |
| **Time** | 45-60 minutes |
| **Copilot Features** | Chat, `@workspace`, `#file`, Enterprise Bing search |

## Objective

Use GitHub Copilot to audit your codebase for security vulnerabilities and performance issues. You'll learn how to prompt Copilot for targeted security analysis (injection attacks, authentication flaws, secrets in code) and performance review (N+1 queries, memory leaks, inefficient algorithms).

## Prerequisites

- Your codebase open in VS Code
- Basic understanding of common vulnerability types (OWASP Top 10)
- Knowledge of your project's performance-sensitive areas

## Your Mission

### Step 1: Security Audit — Input Handling (10 min)

Start with the most common vulnerability category:

```
@workspace Analyze this codebase for input validation and injection vulnerabilities:

1. **SQL Injection** — Are there any raw SQL queries with string concatenation?
2. **XSS** — Is user input rendered in HTML/templates without escaping?
3. **Command Injection** — Is user input passed to system commands?
4. **Path Traversal** — Is user input used in file paths?

For each finding, show the exact file and line, explain the risk, and suggest a fix.
```

### Step 2: Security Audit — Secrets & Auth (10 min)

```
@workspace Check for these security issues:

1. **Hardcoded secrets** — API keys, passwords, tokens, or connection strings in source code
2. **Authentication gaps** — Endpoints or functions accessible without proper authentication
3. **Authorization issues** — Can users access resources that belong to other users?
4. **Sensitive data exposure** — Is PII logged, returned in error messages, or stored insecurely?

For each finding, classify severity (Critical/High/Medium/Low) and suggest a fix.
```

### Step 3: Security Audit — Dependencies (5 min)

```
@workspace Analyze our dependency files (#file:package.json or #file:requirements.txt 
or similar) for potential security concerns:

1. Are there any known-insecure patterns in how we use these libraries?
2. Are there deprecated libraries we should replace?
3. Are we using libraries with known security considerations?
```

### Step 4: Performance Review (15 min)

```
@workspace Analyze this codebase for performance issues:

1. **Database queries** — N+1 queries, missing indexes, fetching more data than needed
2. **Memory** — Large object allocations, leaks, unbounded caches or collections
3. **Algorithms** — O(n²) or worse where O(n) or O(n log n) is possible
4. **I/O** — Synchronous blocking calls, missing connection pooling, no timeout settings
5. **Caching** — Repeated expensive computations that could be cached

For each finding, explain the impact and suggest an optimization.
```

Deep dive on a specific area:

```
@workspace Focus on #file:[performance-critical-file]. 
Profile this code mentally:
- What's the time complexity of the main operations?
- Where would a bottleneck appear under high load?
- What would break first at 100x current traffic?
```

### Step 5: Generate a Findings Report (10 min)

```
Compile all security and performance findings into a report:

# Security & Performance Review — [Date]

## Critical Findings
[Issues requiring immediate attention]

## Security Findings
| # | Severity | File | Issue | Recommendation |
|---|----------|------|-------|----------------|

## Performance Findings
| # | Impact | File | Issue | Recommendation |
|---|--------|------|-------|----------------|

## Summary
- Total findings: X
- Critical: X | High: X | Medium: X | Low: X
```

## Prompt Recipes

| Goal | Prompt |
|------|--------|
| OWASP check | `@workspace Review this project against the OWASP Top 10. Which vulnerabilities might be present?` |
| API security | `@workspace Review our API endpoints for authentication, authorization, rate limiting, and input validation gaps.` |
| Query performance | `Find all database queries in #file:[data-layer] and identify N+1 queries, missing pagination, or unnecessary fetches.` |
| Memory analysis | `@workspace Identify code patterns that could cause memory leaks or excessive memory usage.` |
| Secure defaults | `@workspace Are there any places where insecure defaults are used (HTTP instead of HTTPS, weak encryption, permissive CORS)?` |

## Pro Tips

- **Copilot isn't a security scanner** — It finds common patterns and code smells, but doesn't replace tools like Dependabot, Snyk, or CodeQL. Use it as a complement
- **Be specific about your stack** — "Check for SQL injection in our Express.js app using Sequelize" gets better results than "check for security issues"
- **Fix as you go** — When Copilot identifies an issue, fix it immediately with Inline Chat (`Ctrl+I`) → `Fix this security vulnerability`
- **Use Bing search for current CVEs** — Copilot Enterprise can search the web: "Are there any known security advisories for [library] version [version]?"
- **Check error messages** — Ask Copilot: "Do any error messages in our API responses leak internal implementation details or stack traces?"

## Self-Assessment Checklist

- [ ] I completed a security audit covering input handling, secrets, and auth
- [ ] I completed a performance review covering queries, memory, and algorithms
- [ ] Copilot identified at least 3 actionable findings
- [ ] I fixed or documented at least 2 findings
- [ ] I generated a findings report I could share with my team
- [ ] I understand the limitations of AI-assisted security review

## Going Further

- Run a **real security tool** (Dependabot, CodeQL, Snyk) and compare its findings with Copilot's
- Use the security findings to create tickets in your team's backlog
- Apply Copilot's performance suggestions and **benchmark** before/after
- Feed findings into the [Legacy Code Modernization](challenge-3-legacy-code-modernization.md) challenge
