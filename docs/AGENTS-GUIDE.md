# AI Agents Guide

## 🎯 Understanding OpenCode Agents

**What are Agents?**
Agents in OpenCode are specialized AI personas with specific:
- **Prompts**: Custom instructions and behavior guidelines
- **Tools**: Permission sets for file access, shell commands, etc.
- **Models**: Dedicated or shared AI models
- **Temperature**: Creativity vs determinism settings
- **Verbosity**: Detail level in responses

**Agent Types:**
1. **Primary Agents**: Main conversation agents (cycle with Tab)
2. **Subagents**: Specialized agents invoked via `@mention`
3. **System Agents**: Hidden agents for compaction, titling, etc.

## 🤖 Built-in Agents

### Build Agent (`primary`):
- **Default mode**: Full tool access (write, edit, bash)
- **Purpose**: Implementation and code changes
- **Tools**: All enabled (configurable)
- **Temperature**: 0.1 (deterministic)

### Plan Agent (`primary`):
- **Activation**: Press `Tab` to switch
- **Purpose**: Analysis, planning, brainstorming
- **Tools**: Limited (typically `ask` only by default)
- **Temperature**: 0.3 (slightly creative)

### General Subagent (`subagent`):
- **Invocation**: Automatically for multi-step tasks
- **Purpose**: Complex task execution
- **Tools**: Full access (like Build)
- **Use Case**: "Research and implement X"

### Explore Subagent (`subagent`):
- **Invocation**: For codebase exploration
- **Purpose**: Read-only analysis
- **Tools**: Read-only file access
- **Use Case**: "Explain this codebase"

## 🔄 Agent Workflow Patterns

### Pattern 1: Plan → Build Cycle
```bash
# 1. Start in Plan mode (default or Tab)
[Plan] How would you implement user authentication?

# 2. Review and refine plan
Add JWT token refresh mechanism

# 3. Switch to Build mode (Tab)
[Build] Implement the authentication system as planned
```

### Pattern 2: Multi-Agent Collaboration
```bash
# Use @mentions to invoke specific agents
@explore Analyze the security vulnerabilities in @src/auth/

@general Based on the analysis, create a security fix plan

[Build] Implement the security fixes
```

### Pattern 3: Specialized Task Delegation
```bash
# Create custom agents for specific tasks
@code-reviewer Review @src/components/Button.tsx

@test-writer Write unit tests for @src/utils/validation.ts

@documentation Generate API docs for @src/api/
```

## 🛠️ Creating Custom Agents

### Method 1: Markdown Configuration (Recommended)
```markdown
# ~/.config/opencode/agents/code-reviewer.md

name: Code Reviewer
description: Specialized agent for thorough code reviews
model: claude-sonnet-4.6
temperature: 0.2
verbosity: high

## Instructions
You are a senior code reviewer. Your job is to:
1. Review code for bugs, security issues, and performance problems
2. Suggest improvements following best practices
3. Focus on readability, maintainability, and scalability
4. Provide specific, actionable feedback

## Tools
- read: true
- ask: true
- write: false  # Reviewer doesn't make changes
- edit: false
- bash: false

## Examples
When reviewing authentication code, check for:
- Input validation
- Password hashing
- Session management
- Error handling
```

### Method 2: JSON Configuration
```json
// ~/.config/opencode/agents/code-reviewer.json
{
  "name": "Code Reviewer",
  "description": "Specialized agent for thorough code reviews",
  "prompt": "You are a senior code reviewer...",
  "model": "claude-sonnet-4.6",
  "temperature": 0.2,
  "verbosity": "high",
  "tools": {
    "read": true,
    "ask": true,
    "write": false,
    "edit": false,
    "bash": false
  }
}
```

### Method 3: Project-Specific Agents
```bash
# Create in project root
mkdir -p .opencode/agents
touch .opencode/agents/project-specific.md

# Project agents override global agents
```

## ⚙️ Agent Configuration Options

### Tool Permissions:
```yaml
tools:
  read: true      # Read files
  ask: true       # Ask clarifying questions
  write: true     # Create new files
  edit: true      # Edit existing files
  bash: true      # Execute shell commands
  skill: ["git", "test"]  # Specific skills only
```

### Model Settings:
```yaml
model: gpt-5.2-codex  # Specific model
# or
model_config:
  provider: opencode
  family: claude
  version: sonnet-4.6
```

### Behavior Settings:
```yaml
temperature: 0.1    # 0.0-1.0 (lower = more deterministic)
verbosity: medium   # low, medium, high, verbose
max_tokens: 4000    # Response length limit
thinking: enabled   # Show thinking steps
```

## 🔗 Advanced Agent Patterns

### 1. Chain of Agents:
```bash
# Sequential agent workflow
@explore Analyze the codebase structure

@architect Design the new feature architecture

@implementer Write the implementation code

@tester Create test cases

@reviewer Review the complete implementation
```

### 2. Parallel Agent Teams:
```bash
# Multiple agents working on different aspects
@frontend Implement React components for the UI

@backend Create API endpoints and database models

@devops Set up deployment configuration

@documentation Write user and developer docs
```

### 3. Conditional Agent Routing:
```bash
# Based on task type, route to appropriate agent
If it's a bug fix: @debugger
If it's a new feature: @implementer
If it's documentation: @technical-writer
If it's refactoring: @refactor-specialist
```

## 📋 Agent Management Commands

### List Available Agents:
```bash
/agents
# Shows: Build, Plan, code-reviewer, test-writer, etc.
```

### Switch Agents:
```bash
# Tab cycles between primary agents
Tab

# Direct selection
/agents select code-reviewer
```

### Create New Agent:
```bash
# Interactive creation
/agents create

# Follow prompts for name, description, tools, etc.
```

### Edit Existing Agent:
```bash
# Edit configuration
/agents edit code-reviewer

# Opens in $EDITOR
```

### Delete Agent:
```bash
/agents delete old-agent-name
```

## 📝 Pre-built Agent Examples

### Code Reviewer Agent:
```markdown
# .opencode/agents/code-reviewer.md
name: Code Reviewer
model: claude-sonnet-4.6
temperature: 0.1

## Instructions
You are a meticulous code reviewer. For each file:
1. Check for security vulnerabilities (OWASP Top 10)
2. Verify error handling and edge cases
3. Assess performance implications
4. Review code style and consistency
5. Suggest improvements with examples

Focus on:
- Input validation and sanitization
- Authentication and authorization
- Data privacy and encryption
- Resource management
- Logging and monitoring
```

### Test Writer Agent:
```markdown
# .opencode/agents/test-writer.md
name: Test Writer
model: gpt-5.2-codex
temperature: 0.3

## Instructions
You are a test-driven development expert. Create:
1. Unit tests for individual functions
2. Integration tests for component interactions
3. End-to-end tests for user workflows
4. Performance and load tests
5. Security and penetration tests

Principles:
- Test behavior, not implementation
- Use realistic test data
- Mock external dependencies
- Achieve high coverage
- Follow AAA pattern (Arrange, Act, Assert)
```

### Documentation Agent:
```markdown
# .opencode/agents/documentation.md
name: Documentation Specialist
model: gemini-2.5-pro
temperature: 0.4

## Instructions
You create comprehensive, user-friendly documentation:
1. API documentation with examples
2. User guides with step-by-step instructions
3. Architecture diagrams and explanations
4. Troubleshooting guides
5. Changelogs and release notes

Style:
- Clear, concise language
- Practical examples
- Visual aids when helpful
- Multiple formats (markdown, HTML, PDF-ready)
```

## ⚡ Agent Performance Optimization

### 1. Model Selection:
```yaml
# Match agent to appropriate model
code-reviewer: claude-sonnet-4.6  # Good for analysis
test-writer: gpt-5.2-codex        # Good for code generation
documentation: gemini-2.5-pro     # Good for creative writing
```

### 2. Temperature Tuning:
```yaml
# Lower for deterministic tasks
code-reviewer: 0.1
refactoring: 0.2

# Higher for creative tasks
brainstorming: 0.7
naming: 0.5
```

### 3. Tool Restriction:
```yaml
# Limit tools to prevent accidents
reviewer: [read, ask]           # Read-only review
implementer: [read, write, edit] # Can modify code
admin: [read, write, edit, bash] # Full access
```

### 4. Verbosity Control:
```yaml
# Adjust detail level
debugging: verbose    # Show all reasoning steps
production: medium    # Balanced detail
automation: low       # Minimal output
```

## 🎯 Agent Best Practices

### 1. Start Simple:
- Begin with basic agents (reviewer, implementer)
- Add complexity gradually
- Test each agent thoroughly

### 2. Clear Prompts:
- Be specific about agent's role
- Include examples of good output
- Define boundaries and limitations

### 3. Security First:
- Restrict bash access for sensitive agents
- Use project-specific agents for client work
- Review agent permissions regularly

### 4. Performance Monitoring:
- Track token usage per agent
- Monitor response times
- Adjust models based on performance

### 5. Iterative Improvement:
- Collect feedback from agent usage
- Refine prompts based on results
- Share successful agents with team

## 🔧 Common Agent Use Cases

### Code Review Workflow:
```bash
# 1. Create PR with changes
!git checkout -b feature/new-auth
# ... make changes ...

# 2. Run code review
@code-reviewer Review all changed files

# 3. Address feedback
[Build] Fix the security issues identified

# 4. Run tests
@test-writer Add tests for the new authentication

# 5. Final review
@code-reviewer Verify all issues are resolved
```

### Feature Development Workflow:
```bash
# 1. Planning phase
@explore Analyze current codebase structure
@architect Design new feature architecture

# 2. Implementation phase
@frontend Implement UI components
@backend Create API endpoints
@database Design database schema

# 3. Testing phase
@test-writer Create comprehensive test suite
@security-reviewer Check for vulnerabilities

# 4. Documentation phase
@documentation Write user and developer docs
```

### Bug Fix Workflow:
```bash
# 1. Diagnosis
@debugger Analyze the bug report and logs
@explore Find related code and dependencies

# 2. Solution design
@architect Design the fix with minimal impact
@reviewer Review the proposed solution

# 3. Implementation
[Build] Implement the fix

# 4. Verification
@test-writer Create regression tests
@reviewer Verify the fix doesn't break anything
```

## 🐛 Troubleshooting Agents

### Common Issues:

**1. Agent not responding**
```bash
# Check agent configuration
/agents list

# Verify model availability
/models
```

**2. Incorrect tool permissions**
```bash
# Check agent tools
/agents show agent-name

# Edit permissions
/agents edit agent-name
```

**3. Poor quality responses**
```bash
# Adjust temperature
/agents edit agent-name
# Set temperature: 0.1-0.3 for code, 0.4-0.7 for creative

# Try different model
/agents edit agent-name
# Change model to better fit task
```

**4. Agent using wrong context**
```bash
# Be specific in invocation
@agent-name Please review @specific-file.ts

# Provide clear boundaries
Focus only on security aspects, not code style
```

### Debug Commands:
```bash
# See agent thinking process
/thinking on

# Check agent configuration
!cat ~/.config/opencode/agents/agent-name.md

# Test agent with simple task
@agent-name What's 2+2?
```

> **💡 Pro Tip**: Create a "debug" agent with verbose output and thinking enabled to understand how other agents are working. This is invaluable for troubleshooting complex agent interactions.

## 📚 Agent Templates Repository

Consider creating a repository of agent templates for common tasks:

```
agents-templates/
├── code-review/
│   ├── security-reviewer.md
│   ├── performance-reviewer.md
│   └── style-reviewer.md
├── development/
│   ├── frontend-developer.md
│   ├── backend-developer.md
│   └── fullstack-developer.md
├── testing/
│   ├── unit-test-writer.md
│   ├── integration-test-writer.md
│   └── e2e-test-writer.md
└── documentation/
    ├── api-docs-writer.md
    ├── user-guide-writer.md
    └── architecture-docs-writer.md
```

Share these with your team for consistent AI-assisted development across projects.

---

## 📚 What's Next?

- [Skills Guide](SKILLS-GUIDE.md) - Create reusable workflows
- [Workflows Guide](WORKFLOWS.md) - Design development workflows
- [MCP Guide](MCP-GUIDE.md) - Extend OpenCode with servers
- [Back to Main Guide](../README.md)

---

*Last updated: February 2026*