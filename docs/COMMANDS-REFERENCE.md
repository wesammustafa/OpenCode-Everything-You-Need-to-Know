# Commands Reference Guide

## 🎯 Overview
OpenCode's command system provides powerful control over your AI-assisted development workflow. This guide covers all built-in and custom commands.

## 📋 Built-in Slash Commands

### Essential Commands:

| Command | Purpose | Example |
|---------|---------|---------|
| `/help` | Show help and available commands | `/help` |
| `/connect` | Add or configure LLM providers | `/connect` |
| `/init` | Initialize project with AGENTS.md | `/init` |
| `/undo` | Undo last change (Git-based) | `/undo` |
| `/redo` | Redo last undone change | `/redo` |
| `/share` | Create shareable conversation link | `/share` |
| `/export` | Export conversation to markdown | `/export` |
| `/compact` | Summarize long conversation | `/compact` |
| `/editor` | Open external editor for message | `/editor` |

### Provider & Model Commands:

| Command | Purpose | Example |
|---------|---------|---------|
| `/models` | List available models | `/models` |
| `/sessions` | Manage conversation sessions | `/sessions` |
| `/thinking` | Toggle thinking steps display | `/thinking off` |
| `/themes` | Change TUI theme | `/themes` |
| `/config` | View/edit configuration | `/config` |

### Agent Commands:

| Command | Purpose | Example |
|---------|---------|---------|
| `/agents` | List available agents | `/agents` |
| `/agents select` | Switch to specific agent | `/agents select code-reviewer` |
| `/agents create` | Create new agent | `/agents create` |
| `/agents edit` | Edit agent configuration | `/agents edit reviewer` |
| `/agents delete` | Remove agent | `/agents delete old-agent` |

### Skill Commands:

| Command | Purpose | Example |
|---------|---------|---------|
| `/skills` | List available skills | `/skills` |
| `/skills install` | Install new skill | `/skills install url` |
| `/skills update` | Update skills | `/skills update` |
| `/skills test` | Test skill execution | `/skills test review` |

## 💻 CLI Commands

### Basic CLI Usage:
```bash
# Start interactive TUI
opencode

# Run single command non-interactively
opencode run "Fix the bug in @src/utils/validation.ts"

# Start in specific directory
opencode /path/to/project

# Use specific model
opencode --model gpt-5.2-codex
```

### Advanced CLI Commands:

| Command | Purpose | Example |
|---------|---------|---------|
| `opencode serve` | Start headless HTTP server | `opencode serve --port 8080` |
| `opencode web` | Start web interface | `opencode web` |
| `opencode stats` | Show usage statistics | `opencode stats` |
| `opencode github` | GitHub integration | `opencode github install` |
| `opencode agent` | Agent management | `opencode agent create` |
| `opencode models` | Model management | `opencode models list` |

### Server Mode:
```bash
# Start headless server
opencode serve --port 3000 --host 0.0.0.0

# API endpoints:
# POST /v1/chat - Send message
# GET /v1/status - Server status
# GET /v1/models - Available models

# Example curl request:
curl -X POST http://localhost:3000/v1/chat \
  -H "Content-Type: application/json" \
  -d '{"message": "Hello OpenCode", "model": "gpt-5.2-codex"}'
```

### Web Interface:
```bash
# Start web server
opencode web

# Open in browser: http://localhost:3000
# Provides web-based TUI interface
```

## 🛠️ Creating Custom Commands

### Method 1: Markdown Commands
```markdown
# .opencode/commands/analyze.md

# Code Analysis Command

Analyze code for performance issues and suggest optimizations.

## Usage
```bash
/analyze [file]
```

## Behavior
1. Analyze specified file for performance bottlenecks
2. Identify memory leaks and CPU-intensive operations
3. Suggest optimizations with code examples
4. Provide benchmarking recommendations

## Examples
```bash
/analyze @src/utils/processing.ts
/analyze @src/ --focus memory
```
```

### Method 2: JSON Configuration
```json
// .opencode/commands/optimize.json
{
  "name": "optimize",
  "description": "Optimize code performance",
  "command": "analyze the code in $1 for optimization opportunities",
  "tools": ["read", "ask"],
  "agent": "performance-reviewer"
}
```

### Method 3: Shell Script Commands
```bash
# .opencode/commands/deploy.sh
#!/bin/bash
# Custom deploy command
echo "Starting deployment..."
!git push origin main
!npm run build
!docker build -t myapp .
echo "Deployment complete!"
```

### Command Arguments:
```markdown
# Command with arguments
## Behavior
- $ARGUMENTS: All arguments as string
- $1, $2, $3: Positional arguments
- $OPTIONS: Parsed options

## Examples
```bash
/command arg1 arg2 --option value
# $ARGUMENTS = "arg1 arg2 --option value"
# $1 = "arg1", $2 = "arg2"
```
```

## 🔗 Command Chaining & Pipelines

### Sequential Commands:
```bash
# Run commands in sequence
/init && /analyze @src/ && /review changed
```

### Conditional Execution:
```bash
# Run command only if previous succeeded
/test @src/ && /deploy

# Run alternative on failure
/test @src/ || /fix-tests
```

### Command Output Piping:
```bash
# Use output of one command as input to another
!git status | /analyze-changes

# Capture and reuse output
OUTPUT=$(/analyze @src/)
echo "Analysis complete: $OUTPUT"
```

## ⚡ Advanced Command Patterns

### 1. Interactive Commands:
```markdown
# .opencode/commands/setup.md

# Interactive Setup Command

## Behavior
1. Ask for project type (React, Node.js, Python, etc.)
2. Request framework preferences
3. Configure testing setup
4. Set up deployment configuration
5. Generate project structure

## Interactive Prompts
- "What type of project are you creating?"
- "Which testing framework would you like?"
- "Do you need Docker configuration?"
```
```bash
# Usage
/setup
# Follow interactive prompts
```

### 2. File Generation Commands:
```markdown
# .opencode/commands/generate.md

# File Generation Command

## Behavior
1. Create component/file based on template
2. Apply project-specific conventions
3. Generate tests for the component
4. Update index files/exports
5. Create documentation stub

## Templates
- component: React/Vue component
- api: API endpoint handler
- util: Utility function
- test: Test file
```
```bash
# Usage
/generate component Button
/generate api users --method GET
```

### 3. Workflow Automation Commands:
```markdown
# .opencode/commands/workflow.md

# Complete Development Workflow

## Behavior
1. Check current git status
2. Create feature branch
3. Implement feature using TDD
4. Run tests and fix issues
5. Create pull request
6. Request code review

## Steps
```bash
!git checkout -b feature/$1
/tdd "Implement $1"
/test
/pr
/review
```
```
```bash
# Usage
/workflow "user-authentication"
```

## 🔒 Command Security & Permissions

### Permission Levels:
```yaml
# Command permission configuration
permissions:
  read: true      # Can read files
  write: true     # Can write files
  edit: true      # Can edit files
  bash: true      # Can execute shell commands
  network: false  # Can make network requests
  env: false      # Can access environment variables
```

### Secure Command Design:
```markdown
# Security Guidelines
## Do:
- Validate all input arguments
- Sanitize file paths
- Use minimal required permissions
- Log command execution

## Don't:
- Execute arbitrary shell commands
- Access sensitive environment variables
- Make unauthorized network requests
- Modify system files outside project
```

### Command Auditing:
```bash
# Enable command audit logging
export OPENCODE_AUDIT_LOG=/var/log/opencode-commands.log

# View command history
!cat ~/.local/share/opencode/command-history.log

# Audit specific user/command
grep "user@example.com" /var/log/opencode-commands.log | grep "/deploy"
```

## ⚡ Command Performance Optimization

### Caching Commands:
```bash
# Cache expensive command results
if [ ! -f /tmp/analysis-cache.json ]; then
  /analyze @src/ > /tmp/analysis-cache.json
fi
cat /tmp/analysis-cache.json
```

### Parallel Command Execution:
```bash
# Run commands in parallel
/analyze @src/components/ &
/analyze @src/utils/ &
/analyze @src/api/ &
wait
echo "All analyses complete"
```

### Incremental Commands:
```markdown
# Incremental Analysis Command

## Behavior
1. Check for previous analysis results
2. Only analyze changed files since last run
3. Merge new results with cached results
4. Update cache with latest analysis

## Cache Management
- Store results in .opencode/cache/
- Use file modification times
- Invalidate cache on dependency changes
```

## 🧪 Command Testing & Validation

### Unit Testing Commands:
```bash
# Test command with sample input
/commands test analyze --input @test-data.json

# Test command output validation
/commands test deploy --expected "Deployment successful"

# Test command error handling
/commands test analyze --error "File not found"
```

### Integration Testing:
```bash
# Test command in CI/CD pipeline
opencode run "/test @src/" > test-results.json
if [ $? -eq 0 ]; then
  echo "Tests passed"
else
  echo "Tests failed"
  exit 1
fi
```

### Performance Testing:
```bash
# Benchmark command execution time
time opencode run "/analyze @src/"

# Profile command resource usage
/commands profile optimize --memory --cpu
```

## 📖 Command Documentation

### Command Help System:
```markdown
# .opencode/commands/analyze.md

# Code Analysis Command

## Description
Analyzes code for performance issues, security vulnerabilities, and optimization opportunities.

## Syntax
```bash
/analyze [options] <file|directory>
```

## Options
- `--focus <area>`: Focus on specific area (performance, security, style)
- `--output <format>`: Output format (markdown, json, html)
- `--verbose`: Enable detailed output
- `--fix`: Automatically fix issues where possible

## Examples
### Basic usage
```bash
/analyze @src/utils/validation.ts
```

### Focus on security
```bash
/analyze @src/ --focus security
```

### Output as JSON
```bash
/analyze @src/api/ --output json
```

## Exit Codes
- 0: Success
- 1: Analysis failed
- 2: Invalid arguments
- 3: File not found

## See Also
- [/review](#review): Code review command
- [/test](#test): Testing command
- [/audit](#audit): Security audit command
```

### Auto-generated Documentation:
```bash
# Generate command documentation
/commands docs --output docs/commands.md

# Update command help
/commands update-help

# Validate command documentation
/commands validate-docs
```

## 🌐 Command Ecosystem Management

### Command Registry:
```bash
# Register custom commands
/commands register ./custom-commands/

# List registered commands
/commands list --registered

# Search commands
/commands search "analysis"

# Command categories
/commands list --category development
/commands list --category testing
/commands list --category deployment
```

### Command Versioning:
```markdown
# Command version metadata
---
name: "analyze"
version: "2.1.0"
changelog: |
  v2.1.0: Added security scanning
  v2.0.0: Performance improvements
  v1.0.0: Initial release
compatibility: "opencode>=1.5.0"
dependencies:
  - "review>=1.2.0"
  - "test>=1.1.0"
---
```

### Command Dependencies:
```yaml
# Command dependency management
dependencies:
  required:
    - git
    - node
    - npm
  optional:
    - docker
    - aws-cli
  conflicts:
    - old-analyze-command
```

## 🐛 Troubleshooting Commands

### Common Issues:

**1. Command not found**
```bash
# Check command location
ls -la .opencode/commands/

# Reload commands
/commands reload

# Check command permissions
chmod +x .opencode/commands/command.sh
```

**2. Command execution failed**
```bash
# Enable debug mode
/commands run command-name --debug

# Check command logs
!cat ~/.local/share/opencode/command-debug.log

# Test command manually
!bash .opencode/commands/command.sh --test
```

**3. Permission errors**
```bash
# Check command permissions
/commands permissions command-name

# Run with elevated permissions (careful!)
/commands run command-name --sudo
```

**4. Command conflicts**
```bash
# List conflicting commands
/commands conflicts

# Disable conflicting command
/commands disable old-command
```

### Debug Commands:
```bash
# Dry run command
/commands run command-name --dry-run

# Step through command execution
/commands run command-name --step

# Profile command performance
/commands run command-name --profile

# Trace command execution
/commands run command-name --trace
```

### Command Recovery:
```bash
# Backup command configuration
/commands backup --output commands-backup.tar.gz

# Restore commands from backup
/commands restore commands-backup.tar.gz

# Reset commands to default
/commands reset --confirm
```

> **💡 Pro Tip**: Create a "command-tester" command that validates other commands. This helps maintain command quality and catch issues before they affect your workflow.

## 🎯 Best Practices for Command Design

### 1. Keep Commands Focused:
- One command, one responsibility
- Clear input/output expectations
- Minimal side effects

### 2. Design for Composability:
- Output that can be piped to other commands
- Standard exit codes and error messages
- Consistent argument parsing

### 3. Prioritize Security:
- Validate all inputs
- Use principle of least privilege
- Log command execution for audit

### 4. Ensure Reliability:
- Handle errors gracefully
- Provide clear error messages
- Include rollback mechanisms

### 5. Optimize Performance:
- Cache expensive operations
- Support incremental execution
- Provide progress feedback

### 6. Maintain Documentation:
- Clear usage examples
- Comprehensive help text
- Version compatibility notes

By following these best practices, you can create robust, reliable commands that enhance your OpenCode workflow without introducing complexity or security risks.

---

## 📚 What's Next?

- [MCP Guide](MCP-GUIDE.md) - Extend OpenCode with servers
- [Workflows Guide](WORKFLOWS.md) - Design development workflows
- [FAQ & Troubleshooting](FAQ-TROUBLESHOOTING.md) - Common issues and solutions
- [Back to Main Guide](../README.md)

---

*Last updated: February 2026*