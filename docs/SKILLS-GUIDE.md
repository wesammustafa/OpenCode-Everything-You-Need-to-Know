# Skills System Guide

## 🎯 What Are OpenCode Skills?
**Skills** are reusable behavior definitions that transform complex workflows into simple, repeatable commands. Think of them as "macros for AI" that encapsulate multi-step processes into single invocations.

### Key Characteristics:
1. **Reusable**: Define once, use everywhere
2. **Shareable**: Commit to version control, share with team
3. **Customizable**: Modify for specific projects or workflows
4. **Secure**: Permission-controlled execution
5. **Discoverable**: Auto-listed in OpenCode interface

## 📁 Skill File Structure

### Basic SKILL.md Template:
```markdown
---
name: "Skill Name"
description: "Brief description of what this skill does"
version: "1.0.0"
license: "MIT"
compatibility: "opencode>=1.5.0"
tools: ["read", "ask", "write", "edit", "bash"]
permissions: ["project", "global"]
---

# Skill Name

Detailed description of the skill's purpose and behavior.

## Behavior
- Step 1: What OpenCode should do first
- Step 2: Next action to take
- Step 3: Final steps and cleanup

## Guidelines
- Best practices to follow
- Constraints or requirements
- Error handling procedures

## Examples
### Example 1: Basic Usage
```bash
/skill-name argument1 argument2
```

### Example 2: Advanced Usage
```bash
/skill-name --option value @file.ts
```

## Notes
- Additional information
- Troubleshooting tips
- Related skills
```

## 🚀 Creating Your First Skill

### Step 1: Create Skill Directory
```bash
# Global skills (available in all projects)
mkdir -p ~/.config/opencode/skills

# Project-specific skills (recommended for teams)
mkdir -p .opencode/skills
```

### Step 2: Create Skill File
```bash
# Create a simple code review skill
cat > .opencode/skills/review.md << 'EOF'
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
EOF
```

### Step 3: Test Your Skill
```bash
# Start OpenCode
opencode

# Use your new skill
/review @src/utils/validation.ts
```

## 📋 Available Skill Categories

### 🔹 Development Workflow

**`/pr` - Pull Request Creation**
- Creates feature branch from current changes
- Formats code using project formatters
- Splits changes into logical commits
- Generates descriptive commit messages
- Creates PR with summary and test plan

**`/tdd` - Test-Driven Development**
- Enforces Red-Green-Refactor cycle
- Creates failing tests first
- Implements minimal solution
- Refactors for quality
- Maintains feature notes

**`/refactor` - Code Refactoring**
- Analyzes code for improvement opportunities
- Suggests refactoring strategies
- Implements changes safely
- Preserves functionality
- Updates tests as needed

### 🔹 Quality Assurance

**`/review` - Code Review**
- Multi-perspective review (security, performance, style)
- Actionable recommendations
- Code examples for fixes
- Priority-based feedback

**`/test` - Test Generation**
- Creates comprehensive test suites
- Covers edge cases and error conditions
- Follows testing best practices
- Integrates with project test framework

**`/audit` - Security Audit**
- Security vulnerability scanning
- Dependency vulnerability check
- Configuration security review
- Compliance verification

### 🔹 Project Management

**`/todo` - Task Management**
- Manages project todos in `todos.md`
- Supports due dates and priorities
- Tracks completion status
- Generates progress reports

**`/docs` - Documentation**
- Generates API documentation
- Creates user guides
- Updates README files
- Maintains changelogs

**`/plan` - Project Planning**
- Creates development plans
- Estimates effort and complexity
- Identifies dependencies and risks
- Generates timeline estimates

## 📝 Skill Examples

### Complete PR Skill:
```markdown
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
```

### Complete TDD Skill:
```markdown
---
name: "Test-Driven Development"
description: "Complete TDD workflow with Red-Green-Refactor cycle"
version: "1.0.0"
tools: ["read", "write", "edit", "bash"]
permissions: ["project"]
---

# Test-Driven Development

Implements features using strict Test-Driven Development methodology.

## Behavior
1. **RED**: Write failing test for desired feature
2. **GREEN**: Implement minimal code to pass test
3. **REFACTOR**: Improve code while keeping tests green
4. Repeat for each requirement
5. Maintain feature notes in `notes/features/`

## TDD Principles
- Write tests first, code second
- Minimal implementation to pass tests
- Refactor only when tests are green
- One assertion per test (ideally)
- Test behavior, not implementation

## Examples
### Start TDD for new feature
```bash
/tdd "User registration with email validation"
```

### Continue TDD session
```bash
/tdd continue
```

### TDD with specific test framework
```bash
/tdd --framework jest "API endpoint testing"
```
```

## 📋 Skill Management

### Listing Skills:
```bash
# See available skills
/skills list

# Filter by category
/skills list --category development

# Search skills
/skills search "review"
```

### Skill Information:
```bash
# View skill details
/skills show review

# Check skill permissions
/skills permissions pr
```

### Skill Installation:
```bash
# Install from URL
/skills install https://github.com/user/repo/skills/review.md

# Install from local file
/skills install ./custom-skills/audit.md

# Install from directory
/skills install ./skills-directory/
```

### Skill Updates:
```bash
# Update all skills
/skills update

# Update specific skill
/skills update review

# Check for updates
/skills check-updates
```

## ⚡ Advanced Skill Features

### 1. Skill Arguments:
```markdown
## Behavior
- Use $ARGUMENTS for all arguments
- Use $1, $2, $3 for positional arguments
- Use $OPTIONS for parsed options

## Examples
```bash
/skill-name arg1 arg2 --option value
# $ARGUMENTS = "arg1 arg2 --option value"
# $1 = "arg1", $2 = "arg2"
```
```

### 2. Shell Command Integration:
```markdown
## Behavior
- Execute shell commands with !command
- Capture output for use in skill
- Handle command failures gracefully

## Examples
```bash
# Get git status
!git status

# Check Node.js version
!node --version
```
```

### 3. File References:
```markdown
## Behavior
- Reference files with @filename
- Support fuzzy file search
- Handle multiple file references

## Examples
```bash
# Review specific file
/review @src/auth/index.ts

# Compare files
/compare @old-version.ts @new-version.ts
```
```

### 4. Agent & Model Overrides:
```markdown
---
model: "claude-sonnet-4.6"
temperature: 0.1
agent: "code-reviewer"
---

# Skill uses specific model and agent
```

## 🔒 Skill Security Best Practices

### 1. Permission Management:
- Use minimal required permissions
- Restrict bash access for sensitive skills
- Review third-party skills before installation

### 2. Input Validation:
- Validate skill arguments
- Sanitize file paths
- Handle edge cases gracefully

### 3. Error Handling:
- Provide clear error messages
- Log skill execution
- Roll back changes on failure

### 4. Testing Skills:
```bash
# Test skill in safe environment
/skills test review --dry-run

# Test with sample data
/skills test audit --sample @test-data.json
```

## 🏗️ Creating Skill Templates

### Skill Template Repository Structure:
```
skills-templates/
├── development/
│   ├── pr-template.md
│   ├── tdd-template.md
│   └── refactor-template.md
├── quality/
│   ├── review-template.md
│   ├── test-template.md
│   └── audit-template.md
├── project/
│   ├── todo-template.md
│   ├── docs-template.md
│   └── plan-template.md
└── README.md
```

### Template Usage:
```bash
# Create skill from template
/skills create-from-template development/pr-template.md my-pr-skill

# Customize template
cp skills-templates/development/pr-template.md .opencode/skills/my-pr.md
# Edit my-pr.md for project specifics
```

## 🤝 Skill Sharing & Collaboration

### Team Skill Repository:
```bash
# Clone team skills
git clone https://github.com/team/skills-repo.git
ln -s skills-repo/skills .opencode/skills

# Update team skills
cd .opencode/skills && git pull

# Contribute new skills
cd .opencode/skills
git add new-skill.md
git commit -m "Add new code review skill"
git push
```

### Skill Versioning:
```markdown
---
name: "Code Review"
description: "Comprehensive code review"
version: "1.2.0"
changelog: |
  v1.2.0: Added security scanning
  v1.1.0: Improved performance analysis
  v1.0.0: Initial release
compatibility: "opencode>=1.5.0"
---
```

### Skill Documentation:
```markdown
## Documentation
### Usage
```bash
/skill-name [options] [arguments]
```

### Options
- `--focus <area>`: Focus on specific area (security, performance, style)
- `--output <format>`: Output format (markdown, json, html)
- `--verbose`: Enable verbose output

### Examples
See [EXAMPLES.md](EXAMPLES.md) for more examples.

### Support
Report issues at: https://github.com/team/skills-repo/issues
```

## 🐛 Troubleshooting Skills

### Common Issues:

**1. Skill not found**
```bash
# Check skill location
ls -la .opencode/skills/

# Reload skills
/skills reload
```

**2. Permission errors**
```bash
# Check skill permissions
/skills permissions skill-name

# Run with elevated permissions (careful!)
/skills run skill-name --permissions elevated
```

**3. Skill execution failed**
```bash
# Enable debug mode
/skills run skill-name --debug

# Check skill logs
!cat ~/.local/share/opencode/skills.log
```

**4. Skill conflicts**
```bash
# List conflicting skills
/skills conflicts

# Disable conflicting skill
/skills disable old-skill
```

### Debug Commands:
```bash
# Dry run skill
/skills run skill-name --dry-run

# Step through skill execution
/skills run skill-name --step

# Profile skill performance
/skills run skill-name --profile
```

> **💡 Pro Tip**: Create a "skill-tester" skill that validates other skills. This helps maintain quality and catch issues before they affect your workflow.

## 🌐 Skill Ecosystem

Consider building a skill ecosystem for your organization:

### Central Skill Registry:
- Curated list of approved skills
- Version control and changelogs
- Quality assurance process
- Team skill ratings and reviews

### Skill Development Workflow:
1. **Proposal**: Suggest new skill idea
2. **Development**: Create skill with tests
3. **Review**: Peer review and security audit
4. **Approval**: Add to central registry
5. **Distribution**: Deploy to team projects

### Skill Metrics:
- Usage statistics per skill
- Performance metrics
- User satisfaction ratings
- Bug reports and fixes

By building a robust skill ecosystem, you can standardize workflows, improve quality, and accelerate development across your entire organization.

---

## 📚 What's Next?

- [Commands Reference](COMMANDS-REFERENCE.md) - Complete command list
- [Workflows Guide](WORKFLOWS.md) - Design development workflows
- [MCP Guide](MCP-GUIDE.md) - Extend OpenCode with servers
- [Back to Main Guide](../README.md)

---

*Last updated: February 2026*