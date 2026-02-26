---
name: "Code Review"
description: "Comprehensive code review with security, performance, and style checks"
version: "1.0.0"
tools: ["read", "ask"]
permissions: ["project"]
---

# Code Review

Perform thorough code review focusing on security, performance, and maintainability.

## Behavior
1. Analyze the specified file or directory
2. Check for security vulnerabilities (OWASP Top 10)
3. Review performance implications and bottlenecks
4. Assess code style and consistency
5. Suggest specific improvements with examples
6. Provide actionable recommendations

## Guidelines
- Focus on critical issues first
- Provide code examples for fixes
- Consider project-specific conventions
- Balance perfection with practicality

## Examples
### Review a specific file
```bash
/review @src/auth/index.ts
```

### Review changed files
```bash
/review changed
```

### Review with specific focus
```bash
/review @src/ --focus security
```