---
name: "Create Pull Request"
description: "Automated PR creation with branch management and commit splitting"
version: "1.0.0"
tools: ["read", "write", "edit", "bash"]
permissions: ["project"]
---

# Create Pull Request

Automatically creates a pull request from current changes with proper commit hygiene.

## Behavior
1. Check for uncommitted changes
2. Create feature branch based on current changes
3. Format code using project formatter (Biome/Prettier/ESLint)
4. Analyze changes and split into logical commits
5. Create descriptive commit messages
6. Push branch to remote
7. Create pull request with summary and test plan

## Guidelines for Commit Splitting
- Split by feature, component, or concern
- Keep related changes together
- Separate refactoring from feature work
- Ensure each commit stands alone
- Follow conventional commit format

## Examples
### Basic PR creation
```bash
/pr
```

### PR with specific branch name
```bash
/pr feature/user-authentication
```

### PR with custom description
```bash
/pr --description "Add user authentication with JWT"
```