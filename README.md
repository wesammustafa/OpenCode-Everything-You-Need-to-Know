# OpenCode-Everything-You-Need-to-Know

The ultimate all-in-one guide to mastering OpenCode. From installation, Zen model router setup, TUI mastery, commands, skills, agents, workflows, automation, and integrations, to MCP servers, plugins, and advanced customization—packed with step-by-step tutorials, real-world examples, and expert strategies to make this the global go-to repo for OpenCode mastery.

> **⚠️ IMPORTANT NOTE**  
> To get the best visualization for the documents in this repo, please install [Obsidian](https://obsidian.md/).

### 🧵 What We Covered:

**Fundamentals:**

- [What are LLMs, and how do they differ from AI tools like OpenCode? Why should we use AI tools?](#what-are-llms-and-how-do-they-differ-from-ai-tools-like-opencode)
- [What is OpenCode?](#what-is-opencode)
- [OpenCode Installation: Get up and running with minimal setup.](#opencode-installation)

**Core Features:**

- [Zen Model Router Deep Dive](#zen-model-router-deep-dive)
- [TUI Mastery: Extract the best possible results by leveraging OpenCode's terminal interface capabilities to their fullest.](#tui-mastery)
- [OpenCode Skills: Transform complex workflows into reusable slash commands](#opencode-skills)
- [AI Agents: Harness agents, sub-agents, and build/plan modes to structure intelligence with precision.](#ai-agents)
- [Commands That Work: Discover the power of OpenCode commands and learn how to implement them for maximum impact.](#commands)
- [What are MCP servers and how to use them?](#model-context-protocol-mcp)



### What are LLMs, and how do they differ from AI tools like OpenCode?

**LLM (Large Language Model):**

- This is the underlying AI technology/engine
- Think of it like a car engine - it's the core component that makes everything work
- Examples: GPT-4/5, Claude 4.5/4.6, Gemini, Llama, Mistral (the actual AI models)

**Products built with LLMs:** These are the applications and tools that use LLMs to provide specific services:

**OpenCode:**

- An open-source command-line tool that can use ANY LLM provider
- Specifically designed for developers to code from their terminal with multi-provider support
- It's like having a universal adapter for all AI engines in a developer-focused interface

**Claude Code:**

- A proprietary tool that uses only Claude's LLM
- Limited to Anthropic's ecosystem

**ChatGPT:**

- A web/app interface that uses GPT models
- Designed for general conversations and tasks

**Google Bard/Gemini:**

- Google's chat interface that uses their Gemini LLM
- Note: "Gemini" refers both to Google's LLM and their chat product

**Analogy:**

- **LLM** = Car engine
- **OpenCode** = A universal adapter that can connect to any car engine (built for flexibility)
- **Claude Code** = A specific brand of car (limited to one engine type)
- **ChatGPT** = A family sedan (built for general use)
- **Google Bard** = A racing car

The LLM is the "brain" that understands and generates language, while products like OpenCode are specialized interfaces that make multiple brains accessible for particular use cases.

---

### What is OpenCode?

OpenCode is an open-source, terminal-based AI coding agent that lets developers work with ANY LLM provider directly from their terminal. Think of it as having a universal AI coding assistant that can connect to 75+ different AI models and lives right in your development environment.

Here's what makes it revolutionary in simple terms:

**What it does:**

- You can ask any AI model (GPT, Claude, Gemini, local models) to write code, fix bugs, or explain programming concepts without leaving your terminal
- It can read and work with files in your project directory with full context awareness
- You can delegate entire coding tasks to AI and it will work through them step-by-step
- Supports drag-and-drop image analysis for UI/design references
- Provides shareable conversation links for team collaboration

**Why developers love it:**

- **Multi-Provider Freedom**: No vendor lock-in - use OpenAI, Anthropic, Google, local models, or all of them
- **Zen Model Router**: Curated, optimized models with pay-as-you-go pricing
- **Full Project Context**: AI can see your actual project files and understand the context
- **Extensible Architecture**: Plugins, custom tools, MCP servers, and skills system
- **Open Source**: Full transparency, self-hosting capability, and community-driven development
- **Enterprise Ready**: SSO, centralized config, internal AI gateway support

**Example use cases:**

- "OpenCode, add error handling to this function using GPT-5"
- "Write unit tests for my new feature with Claude Sonnet"
- "Help me refactor this messy code using a local Llama model"
- "Explain what this legacy code does and suggest improvements"

It's essentially like having a team of AI pair programming partners who can jump in and help with coding tasks whenever you need it, using the best model for each specific task.

---

### OpenCode Installation

[![OpenCode](/Images/opencode.png)](https://opencode.ai)

[![OpenCode Installation](/Images/opencode-installation.png)](https://opencode.ai/docs/#install)

#### Quick Install (Recommended)
```bash
curl -fsSL https://opencode.ai/install | bash
```

#### Alternative Methods
**Homebrew (macOS/Linux):**
```bash
brew install anomalyco/tap/opencode
```

**npm/Node.js:**
```bash
npm install -g opencode-ai
```

#### Verify Installation
```bash
opencode --version
```

> **Need more details?** Click the installation image above for complete installation guide.

---

### Zen Model Router Deep Dive

**OpenCode Zen** is the revolutionary model routing service that sets OpenCode apart from all other AI coding tools.

#### What is Zen?

Zen is a curated model gateway that provides:

1. **Verified Models**: Tested and benchmarked models optimized specifically for coding tasks
2. **Quality Assurance**: Works directly with model providers to ensure optimal configuration
3. **Cost Transparency**: Pay-as-you-go pricing with per-1M-token rates (no monthly subscriptions)
4. **No Lock-in**: Works alongside other providers; completely optional
5. **Team Features**: Workspace management, role-based access, model curation
6. **BYOK Support**: Bring Your Own Key for OpenAI/Anthropic while accessing other Zen models

#### Key Specifications

Feature | Specification
--------|--------------
**Model Support** | 75+ providers via AI SDK and Models.dev integration
**Pricing Model** | Pay-as-you-go per token (no monthly commitments)
**Free Models** | MiniMax M2.5 Free, Big Pickle (during beta)
**Cost Example** | GPT 5.2 Codex: $1.75/1M input, $14/1M output
**Team Features** | Workspace management, centralized billing
**BYOK Support** | ✅ Yes (bring your own OpenAI/Anthropic keys)

#### How Zen Works

1. **Sign Up**: Visit [opencode.ai/auth](https://opencode.ai/auth) and create an account
2. **Add Billing**: Add credit card for pay-as-you-go usage
3. **Get API Key**: Copy your unique Zen API key
4. **Configure**: Run `/connect` in OpenCode TUI, select "opencode", paste key
5. **Select Models**: Use `/models` to see available curated models

#### Available Models Through Zen

Model | Input Cost | Output Cost | Best For
------|------------|-------------|----------
**GPT 5.2 Codex** | $1.75/1M | $14/1M | General coding, complex tasks
**Claude Sonnet 4.6** | $3-6/1M | $15-22.50/1M | Reasoning, analysis
**Gemini 2.5 Pro** | $2.50/1M | $10/1M | Multimodal tasks
**Qwen 2.5 Coder** | $0.50/1M | $2/1M | Budget coding, simple tasks
**MiniMax M2.5 Free** | Free | Free | Learning, experimentation

#### When to Use Zen vs Direct Providers

**✅ Use Zen When:**

- You want curated, optimized models for coding
- You prefer pay-as-you-go over monthly subscriptions
- You need access to multiple providers with one API key
- You want the latest models without manual configuration
- You're new to AI coding and want a guided experience

**🔧 Use Direct Providers When:**

- You already have existing API credits
- You need specific model versions not in Zen
- You have enterprise agreements with specific providers
- You're using local/self-hosted models

#### Cost Comparison

Tool | Pricing Model | Monthly Cost (Avg) | Model Flexibility
-----|---------------|-------------------|------------------
**OpenCode Zen** | Pay-as-you-go | $5-50 (based on usage) | 75+ models
**Claude Code Pro** | Subscription | $20/month | Claude only
**Cursor Pro** | Subscription | $20/month | Limited selection
**GitHub Copilot** | Subscription | $10/month | GitHub models only

> **💡 Pro Tip**: Start with Zen's free models (MiniMax M2.5 Free) to learn OpenCode, then upgrade to paid models as needed. The pay-as-you-go model means you only pay for what you use.

#### Setting Up Zen Step-by-Step

**Step 1: Sign Up**
```bash
# After installing OpenCode, run:
opencode
# Then in the TUI:
/connect
```
Select "opencode" and follow the link to [opencode.ai/auth](https://opencode.ai/auth)

**Step 2: Create API Key**
1. Sign in with GitHub, Google, or email
2. Add billing information (credit card)
3. Copy your API key from the dashboard

**Step 3: Configure in OpenCode**
```bash
# Paste your API key when prompted
┌ API key
│ 
└ enter
```

**Step 4: Verify Setup**
```bash
# Check available models
/models

# Test with a simple query
Hello OpenCode! What models are available through Zen?
```

#### Advanced Zen Features

**1. Model Switching**
```bash
# Switch between models on the fly
/models
# Select from the list using arrow keys
```

**2. Usage Monitoring**
```bash
# Check your token usage
!opencode stats
# or in TUI, costs are shown in real-time
```

**3. Team Workspaces**
- Create team workspaces for shared billing
- Set monthly usage limits per team member
- Centralized model curation for consistency

**4. BYOK (Bring Your Own Key)**
- Use your existing OpenAI/Anthropic keys
- Still access Zen's curated models
- Unified billing and management

#### Troubleshooting Zen

**Common Issues:**

1. **"Invalid API key"**: Regenerate key at opencode.ai/auth
2. **"No models available"**: Check billing status, may need to add payment method
3. **"Rate limited"**: Upgrade plan or wait for reset
4. **"Model not responding"**: Try alternative model or check provider status

**Debug Commands:**
```bash
# Check connection status
!opencode models --provider opencode

# Test API key
curl -H "Authorization: Bearer YOUR_API_KEY" https://api.opencode.ai/v1/models
```

> **🚨 SECURITY NOTE**: Never commit your Zen API key to version control. Use environment variables or OpenCode's secure credential storage.

#### Zen vs Traditional Subscriptions

**Traditional Model (Claude Code, Cursor):**
- Monthly subscription ($20/month)
- Limited to specific models
- Pay even if you don't use it
- Vendor lock-in

**Zen Model:**
- Pay per token used
- Access to 75+ models
- No monthly commitment
- Mix and match providers
- Transparent pricing

**Example Cost Calculation:**
- 100,000 tokens input + 50,000 tokens output
- Using GPT 5.2 Codex: (0.1 * $1.75) + (0.05 * $14) = $0.175 + $0.70 = $0.875
- Same usage on Claude Code: $20/month (minimum)

> **📊 Real-World Usage**: Most developers spend $5-20/month with Zen, significantly less than fixed subscriptions, while getting access to better models.

---



### TUI Mastery

OpenCode's Terminal User Interface (TUI) is where the magic happens. Mastering the TUI unlocks OpenCode's full potential for rapid development.

#### TUI Layout Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ OpenCode v1.5.2 │ Project: /Users/you/project │ Model: gpt-5.2-codex        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ You: Can you help me fix the bug in @src/utils/validation.ts?               │
│                                                                             │
│ OpenCode: I'll analyze the validation.ts file and identify the bug...       │
│                                                                             │
│ [Thinking...]                                                               │
│ • Reading file: src/utils/validation.ts                                     │
│ • Analyzing validation logic...                                             │
│ • Found potential issue on line 45...                                       │
│                                                                             │
│ The bug is in the email validation regex. Here's the fix:                   │
│                                                                             │
│ ```typescript                                                               │
│ // Before:                                                                  │
│ const emailRegex = /^[^@]+@[^@]+\.[^@]+$/;                                  │
│                                                                             │
│ // After:                                                                   │
│ const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;      │
│ ```                                                                         │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│ [Build] Press Tab to switch agents • Type /help for commands • Ctrl+C to exit│
└─────────────────────────────────────────────────────────────────────────────┘
```

#### Essential Keyboard Shortcuts

Shortcut | Action | Description
---------|--------|------------
**Tab** | Switch agents | Toggle between Build and Plan modes
**Ctrl+C** | Exit | Exit OpenCode (press twice to force)
**Ctrl+R** | Redo | Redo last undone change
**Ctrl+U** | Undo | Undo last change
**Ctrl+L** | Clear | Clear terminal screen
**Ctrl+K** | Search | Search command history
**↑/↓** | History | Navigate command history
**@** | File search | Fuzzy search for project files
**!** | Shell prefix | Execute shell command
**/** | Command mode | Enter slash command mode
**Esc** | Cancel | Cancel current operation

#### File Reference System

OpenCode's `@` syntax revolutionizes how you reference files:

**Basic File Reference:**
```bash
# Reference a specific file
Can you explain the authentication logic in @src/auth/index.ts?

# Fuzzy search - OpenCode will help you find the file
I need to update the configuration in @config
```

**Multiple File References:**
```bash
# Compare two files
Compare the implementation in @src/old-impl.ts and @src/new-impl.ts

# Analyze entire directory
What's the structure of @src/components/?
```

**Line-Specific References:**
```bash
# Reference specific lines
Check lines 45-60 in @src/utils/validation.ts

# Error location
There's an error on line 123 in @src/api/server.ts
```

#### Shell Command Integration

Execute shell commands directly within OpenCode:

**Basic Shell Commands:**
```bash
# Run any shell command with ! prefix
!ls -la
!git status
!npm install
!docker ps
```

**Command Output in Context:**
```bash
# Use command output in your prompt
!pwd
# OpenCode sees: "/Users/you/project"

Now create a new directory here called "tests"
```

**Chaining Commands:**
```bash
# Multiple commands
!git status && !git diff

# Capture output for analysis
!cat package.json | grep version
What version of React are we using based on the output above?
```

#### Image Analysis

OpenCode can analyze images dragged into the terminal:

**Using Images:**
1. **Drag and drop** any image file into the terminal
2. OpenCode automatically adds it to the prompt
3. Reference the image in your queries

**Example Workflow:**
```bash
# 1. Drag UI mockup into terminal
# 2. OpenCode detects: [Image #1: dashboard-mockup.png]

Create a React component that matches this design [Image #1]
```

**Supported Image Types:**
- PNG, JPEG, GIF, WebP
- Screenshots, mockups, diagrams
- UI designs, architecture diagrams

#### Agent Switching (Build vs Plan)

OpenCode's dual-agent system is its secret weapon:

**Plan Mode (Read-Only):**
- **Activate**: Press `Tab` (shows `[Plan]` in status bar)
- **Purpose**: Analyze, plan, brainstorm without making changes
- **Use Case**: "How would you implement this feature?"

**Build Mode (Read-Write):**
- **Activate**: Press `Tab` (shows `[Build]` in status bar)
- **Purpose**: Make actual code changes
- **Use Case**: "Go ahead and implement the plan"

**Workflow Example:**
```bash
# Start in Plan mode (default)
[Plan] How would you add dark mode to this React app?

# Review the plan, ask questions
What about CSS variables vs Tailwind?

# Switch to Build mode (Tab)
[Build] Sounds good! Implement it.
```

#### Conversation Management

**Session Persistence:**
- Conversations are automatically saved
- Resume where you left off
- Git-based undo/redo system

**Multiple Sessions:**
```bash
# List sessions
/sessions

# Switch sessions
/sessions switch session-name

# Delete session
/sessions delete old-session
```

**Export Conversations:**
```bash
# Export to markdown
/export

# Creates: opencode-conversation-2025-02-26.md
```

#### Advanced TUI Features

**1. Compact Mode:**
```bash
# Summarize long conversations
/compact

# Focus on specific topics
/compact "Focus on the authentication changes"
```

**2. Editor Integration:**
```bash
# Open external editor for long messages
/editor

# Uses $EDITOR environment variable
```

**3. Theme Customization:**
```bash
# Change TUI theme
/themes

# Select from available themes
# Popular: catppuccin, dracula, nord, solarized
```

**4. Real-time Cost Display:**
- Token usage shown in status bar
- Cost estimates for current session
- Provider-specific pricing

#### Productivity Tips

**1. Quick File Navigation:**
```bash
# Use @ with partial names
@utils  # Finds utils/ directory or utils.ts
@.env   # Finds .env files
@test   # Finds test files
```

**2. Command History:**
- Press `↑` to cycle through previous commands
- `Ctrl+K` to search history
- History persists across sessions

**3. Multi-line Input:**
```bash
# Shift+Enter for new lines
This is a multi-line
query that spans
multiple lines
```

**4. Quick Provider Switching:**
```bash
# Change model on the fly
/models

# Select from list
# Changes apply immediately
```

#### Troubleshooting TUI Issues

**Common Issues:**

1. **TUI not rendering properly**
   ```bash
   # Check terminal compatibility
   echo $TERM
   
   # Try different terminal emulator
   # WezTerm or Alacritty recommended
   ```

2. **Input lag or slow response**
   ```bash
   # Check system resources
   !top
   
   # Try lighter model
   /models
   # Select smaller model
   ```

3. **Images not working**
   ```bash
   # Check terminal image support
   # Use WezTerm for best image support
   
   # Alternative: describe image in text
   ```

4. **File references not found**
   ```bash
   # Check current directory
   !pwd
   
   # Use absolute paths if needed
   @/full/path/to/file.ts
   ```

**Performance Optimization:**
```bash
# Use lighter themes
/themes
# Select "minimal" or "simple"

# Disable thinking steps
/thinking off

# Reduce verbosity in agent settings
```

> **💡 Pro Tip**: Master the `Tab` key switching between Plan and Build modes. This single habit will dramatically improve your OpenCode workflow efficiency.

#### TUI Customization

**Keybind Customization:**
```json
// ~/.config/opencode/keybinds.json
{
  "switch_agent": "Tab",
  "exit": ["Ctrl+C", "Ctrl+D"],
  "clear": "Ctrl+L",
  "history_search": "Ctrl+K"
}
```

**Theme Configuration:**
```json
// ~/.config/opencode/themes.json
{
  "current": "catppuccin",
  "custom": {
    "background": "#1e1e2e",
    "foreground": "#cdd6f4",
    "accent": "#89b4fa"
  }
}
```

**Status Bar Customization:**
```json
// ~/.config/opencode/config.json
{
  "ui": {
    "status_bar": {
      "show_cost": true,
      "show_tokens": true,
      "show_model": true,
      "show_agent": true
    }
  }
}
```

The TUI is where OpenCode shines. Spend time mastering these features, and you'll unlock 10x productivity gains in your development workflow.

---

### AI Agents

OpenCode's agent system is one of its most powerful features, enabling sophisticated AI-assisted development workflows.

#### Understanding OpenCode Agents

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

#### Built-in Agents

**Build Agent (`primary`):**
- **Default mode**: Full tool access (write, edit, bash)
- **Purpose**: Implementation and code changes
- **Tools**: All enabled (configurable)
- **Temperature**: 0.1 (deterministic)

**Plan Agent (`primary`):**
- **Activation**: Press `Tab` to switch
- **Purpose**: Analysis, planning, brainstorming
- **Tools**: Limited (typically `ask` only by default)
- **Temperature**: 0.3 (slightly creative)

**General Subagent (`subagent`):**
- **Invocation**: Automatically for multi-step tasks
- **Purpose**: Complex task execution
- **Tools**: Full access (like Build)
- **Use Case**: "Research and implement X"

**Explore Subagent (`subagent`):**
- **Invocation**: For codebase exploration
- **Purpose**: Read-only analysis
- **Tools**: Read-only file access
- **Use Case**: "Explain this codebase"

#### Agent Workflow Patterns

**Pattern 1: Plan → Build Cycle**
```bash
# 1. Start in Plan mode (default or Tab)
[Plan] How would you implement user authentication?

# 2. Review and refine plan
Add JWT token refresh mechanism

# 3. Switch to Build mode (Tab)
[Build] Implement the authentication system as planned
```

**Pattern 2: Multi-Agent Collaboration**
```bash
# Use @mentions to invoke specific agents
@explore Analyze the security vulnerabilities in @src/auth/

@general Based on the analysis, create a security fix plan

[Build] Implement the security fixes
```

**Pattern 3: Specialized Task Delegation**
```bash
# Create custom agents for specific tasks
@code-reviewer Review @src/components/Button.tsx

@test-writer Write unit tests for @src/utils/validation.ts

@documentation Generate API docs for @src/api/
```

#### Creating Custom Agents

**Method 1: Markdown Configuration (Recommended)**
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

**Method 2: JSON Configuration**
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

**Method 3: Project-Specific Agents**
```bash
# Create in project root
mkdir -p .opencode/agents
touch .opencode/agents/project-specific.md

# Project agents override global agents
```

#### Agent Configuration Options

**Tool Permissions:**
```yaml
tools:
  read: true      # Read files
  ask: true       # Ask clarifying questions
  write: true     # Create new files
  edit: true      # Edit existing files
  bash: true      # Execute shell commands
  skill: ["git", "test"]  # Specific skills only
```

**Model Settings:**
```yaml
model: gpt-5.2-codex  # Specific model
# or
model_config:
  provider: opencode
  family: claude
  version: sonnet-4.6
```

**Behavior Settings:**
```yaml
temperature: 0.1    # 0.0-1.0 (lower = more deterministic)
verbosity: medium   # low, medium, high, verbose
max_tokens: 4000    # Response length limit
thinking: enabled   # Show thinking steps
```

#### Advanced Agent Patterns

**1. Chain of Agents:**
```bash
# Sequential agent workflow
@explore Analyze the codebase structure

@architect Design the new feature architecture

@implementer Write the implementation code

@tester Create test cases

@reviewer Review the complete implementation
```

**2. Parallel Agent Teams:**
```bash
# Multiple agents working on different aspects
@frontend Implement React components for the UI

@backend Create API endpoints and database models

@devops Set up deployment configuration

@documentation Write user and developer docs
```

**3. Conditional Agent Routing:**
```bash
# Based on task type, route to appropriate agent
If it's a bug fix: @debugger
If it's a new feature: @implementer
If it's documentation: @technical-writer
If it's refactoring: @refactor-specialist
```

#### Agent Management Commands

**List Available Agents:**
```bash
/agents
# Shows: Build, Plan, code-reviewer, test-writer, etc.
```

**Switch Agents:**
```bash
# Tab cycles between primary agents
Tab

# Direct selection
/agents select code-reviewer
```

**Create New Agent:**
```bash
# Interactive creation
/agents create

# Follow prompts for name, description, tools, etc.
```

**Edit Existing Agent:**
```bash
# Edit configuration
/agents edit code-reviewer

# Opens in $EDITOR
```

**Delete Agent:**
```bash
/agents delete old-agent-name
```

#### Pre-built Agent Examples

**Code Reviewer Agent:**
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

**Test Writer Agent:**
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

**Documentation Agent:**
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

#### Agent Performance Optimization

**1. Model Selection:**
```yaml
# Match agent to appropriate model
code-reviewer: claude-sonnet-4.6  # Good for analysis
test-writer: gpt-5.2-codex        # Good for code generation
documentation: gemini-2.5-pro     # Good for creative writing
```

**2. Temperature Tuning:**
```yaml
# Lower for deterministic tasks
code-reviewer: 0.1
refactoring: 0.2

# Higher for creative tasks
brainstorming: 0.7
naming: 0.5
```

**3. Tool Restriction:**
```yaml
# Limit tools to prevent accidents
reviewer: [read, ask]           # Read-only review
implementer: [read, write, edit] # Can modify code
admin: [read, write, edit, bash] # Full access
```

**4. Verbosity Control:**
```yaml
# Adjust detail level
debugging: verbose    # Show all reasoning steps
production: medium    # Balanced detail
automation: low       # Minimal output
```

#### Agent Best Practices

**1. Start Simple:**
- Begin with basic agents (reviewer, implementer)
- Add complexity gradually
- Test each agent thoroughly

**2. Clear Prompts:**
- Be specific about agent's role
- Include examples of good output
- Define boundaries and limitations

**3. Security First:**
- Restrict bash access for sensitive agents
- Use project-specific agents for client work
- Review agent permissions regularly

**4. Performance Monitoring:**
- Track token usage per agent
- Monitor response times
- Adjust models based on performance

**5. Iterative Improvement:**
- Collect feedback from agent usage
- Refine prompts based on results
- Share successful agents with team

#### Common Agent Use Cases

**Code Review Workflow:**
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

**Feature Development Workflow:**
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

**Bug Fix Workflow:**
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

#### Troubleshooting Agents

**Common Issues:**

1. **Agent not responding**
   ```bash
   # Check agent configuration
   /agents list
   
   # Verify model availability
   /models
   ```

2. **Incorrect tool permissions**
   ```bash
   # Check agent tools
   /agents show agent-name
   
   # Edit permissions
   /agents edit agent-name
   ```

3. **Poor quality responses**
   ```bash
   # Adjust temperature
   /agents edit agent-name
   # Set temperature: 0.1-0.3 for code, 0.4-0.7 for creative
   
   # Try different model
   /agents edit agent-name
   # Change model to better fit task
   ```

4. **Agent using wrong context**
   ```bash
   # Be specific in invocation
   @agent-name Please review @specific-file.ts
   
   # Provide clear boundaries
   Focus only on security aspects, not code style
   ```

**Debug Commands:**
```bash
# See agent thinking process
/thinking on

# Check agent configuration
!cat ~/.config/opencode/agents/agent-name.md

# Test agent with simple task
@agent-name What's 2+2?
```

> **💡 Pro Tip**: Create a "debug" agent with verbose output and thinking enabled to understand how other agents are working. This is invaluable for troubleshooting complex agent interactions.

#### Agent Templates Repository

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

### OpenCode Skills

OpenCode Skills are reusable behavior definitions that transform complex workflows into simple, repeatable commands. Think of them as "macros for AI" that encapsulate multi-step processes into single invocations.

#### What Are OpenCode Skills?

**Skills** (stored as `SKILL.md` files) are markdown documents with YAML frontmatter that define:
- **Name & Description**: What the skill does
- **Behavior**: Step-by-step instructions for OpenCode
- **Tools & Permissions**: What the skill can access
- **Examples**: Demonstration of usage

**Key Characteristics:**
1. **Reusable**: Define once, use everywhere
2. **Shareable**: Commit to version control, share with team
3. **Customizable**: Modify for specific projects or workflows
4. **Secure**: Permission-controlled execution
5. **Discoverable**: Auto-listed in OpenCode interface

#### Skill File Structure

**Basic SKILL.md Template:**
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

#### Creating Your First Skill

**Step 1: Create Skill Directory**
```bash
# Global skills (available in all projects)
mkdir -p ~/.config/opencode/skills

# Project-specific skills (recommended for teams)
mkdir -p .opencode/skills
```

**Step 2: Create Skill File**
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

**Step 3: Test Your Skill**
```bash
# Start OpenCode
opencode

# Use your new skill
/review @src/utils/validation.ts
```

#### Available Skill Categories

**🔹 Development Workflow**

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

**🔹 Quality Assurance**

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

**🔹 Project Management**

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

#### Skill Examples

**Complete PR Skill:**
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

**Complete TDD Skill:**
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

#### Skill Management

**Listing Skills:**
```bash
# See available skills
/skills list

# Filter by category
/skills list --category development

# Search skills
/skills search "review"
```

**Skill Information:**
```bash
# View skill details
/skills show review

# Check skill permissions
/skills permissions pr
```

**Skill Installation:**
```bash
# Install from URL
/skills install https://github.com/user/repo/skills/review.md

# Install from local file
/skills install ./custom-skills/audit.md

# Install from directory
/skills install ./skills-directory/
```

**Skill Updates:**
```bash
# Update all skills
/skills update

# Update specific skill
/skills update review

# Check for updates
/skills check-updates
```

#### Advanced Skill Features

**1. Skill Arguments:**
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

**2. Shell Command Integration:**
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

**3. File References:**
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

**4. Agent & Model Overrides:**
```markdown
---
model: "claude-sonnet-4.6"
temperature: 0.1
agent: "code-reviewer"
---

# Skill uses specific model and agent
```

#### Skill Security Best Practices

**1. Permission Management:**
- Use minimal required permissions
- Restrict bash access for sensitive skills
- Review third-party skills before installation

**2. Input Validation:**
- Validate skill arguments
- Sanitize file paths
- Handle edge cases gracefully

**3. Error Handling:**
- Provide clear error messages
- Log skill execution
- Roll back changes on failure

**4. Testing Skills:**
```bash
# Test skill in safe environment
/skills test review --dry-run

# Test with sample data
/skills test audit --sample @test-data.json
```

#### Creating Skill Templates

**Skill Template Repository Structure:**
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

**Template Usage:**
```bash
# Create skill from template
/skills create-from-template development/pr-template.md my-pr-skill

# Customize template
cp skills-templates/development/pr-template.md .opencode/skills/my-pr.md
# Edit my-pr.md for project specifics
```

#### Skill Sharing & Collaboration

**Team Skill Repository:**
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

**Skill Versioning:**
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

**Skill Documentation:**
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

#### Troubleshooting Skills

**Common Issues:**

1. **Skill not found**
   ```bash
   # Check skill location
   ls -la .opencode/skills/
   
   # Reload skills
   /skills reload
   ```

2. **Permission errors**
   ```bash
   # Check skill permissions
   /skills permissions skill-name
   
   # Run with elevated permissions (careful!)
   /skills run skill-name --permissions elevated
   ```

3. **Skill execution failed**
   ```bash
   # Enable debug mode
   /skills run skill-name --debug
   
   # Check skill logs
   !cat ~/.local/share/opencode/skills.log
   ```

4. **Skill conflicts**
   ```bash
   # List conflicting skills
   /skills conflicts
   
   # Disable conflicting skill
   /skills disable old-skill
   ```

**Debug Commands:**
```bash
# Dry run skill
/skills run skill-name --dry-run

# Step through skill execution
/skills run skill-name --step

# Profile skill performance
/skills run skill-name --profile
```

> **💡 Pro Tip**: Create a "skill-tester" skill that validates other skills. This helps maintain quality and catch issues before they affect your workflow.

#### Skill Ecosystem

Consider building a skill ecosystem for your organization:

**Central Skill Registry:**
- Curated list of approved skills
- Version control and changelogs
- Quality assurance process
- Team skill ratings and reviews

**Skill Development Workflow:**
1. **Proposal**: Suggest new skill idea
2. **Development**: Create skill with tests
3. **Review**: Peer review and security audit
4. **Approval**: Add to central registry
5. **Distribution**: Deploy to team projects

**Skill Metrics:**
- Usage statistics per skill
- Performance metrics
- User satisfaction ratings
- Bug reports and fixes

By building a robust skill ecosystem, you can standardize workflows, improve quality, and accelerate development across your entire organization.

---

### Commands

OpenCode's command system provides powerful control over your AI-assisted development workflow. Commands range from basic navigation to advanced configuration and automation.

#### Built-in Slash Commands

**Essential Commands:**

Command | Purpose | Example
--------|---------|--------
`/help` | Show help and available commands | `/help`
`/connect` | Add or configure LLM providers | `/connect`
`/init` | Initialize project with AGENTS.md | `/init`
`/undo` | Undo last change (Git-based) | `/undo`
`/redo` | Redo last undone change | `/redo`
`/share` | Create shareable conversation link | `/share`
`/export` | Export conversation to markdown | `/export`
`/compact` | Summarize long conversation | `/compact`
`/editor` | Open external editor for message | `/editor`

**Provider & Model Commands:**

Command | Purpose | Example
--------|---------|--------
`/models` | List available models | `/models`
`/sessions` | Manage conversation sessions | `/sessions`
`/thinking` | Toggle thinking steps display | `/thinking off`
`/themes` | Change TUI theme | `/themes`
`/config` | View/edit configuration | `/config`

**Agent Commands:**

Command | Purpose | Example
--------|---------|--------
`/agents` | List available agents | `/agents`
`/agents select` | Switch to specific agent | `/agents select code-reviewer`
`/agents create` | Create new agent | `/agents create`
`/agents edit` | Edit agent configuration | `/agents edit reviewer`
`/agents delete` | Remove agent | `/agents delete old-agent`

**Skill Commands:**

Command | Purpose | Example
--------|---------|--------
`/skills` | List available skills | `/skills`
`/skills install` | Install new skill | `/skills install url`
`/skills update` | Update skills | `/skills update`
`/skills test` | Test skill execution | `/skills test review`

#### CLI Commands

**Basic CLI Usage:**
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

**Advanced CLI Commands:**

Command | Purpose | Example
--------|---------|--------
`opencode serve` | Start headless HTTP server | `opencode serve --port 8080`
`opencode web` | Start web interface | `opencode web`
`opencode stats` | Show usage statistics | `opencode stats`
`opencode github` | GitHub integration | `opencode github install`
`opencode agent` | Agent management | `opencode agent create`
`opencode models` | Model management | `opencode models list`

**Server Mode:**
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

**Web Interface:**
```bash
# Start web server
opencode web

# Open in browser: http://localhost:3000
# Provides web-based TUI interface
```

#### Custom Commands

**Creating Custom Commands:**

**Method 1: Markdown Commands**
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

**Method 2: JSON Configuration**
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

**Method 3: Shell Script Commands**
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

**Command Arguments:**
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

#### Command Chaining & Pipelines

**Sequential Commands:**
```bash
# Run commands in sequence
/init && /analyze @src/ && /review changed
```

**Conditional Execution:**
```bash
# Run command only if previous succeeded
/test @src/ && /deploy

# Run alternative on failure
/test @src/ || /fix-tests
```

**Command Output Piping:**
```bash
# Use output of one command as input to another
!git status | /analyze-changes

# Capture and reuse output
OUTPUT=$(/analyze @src/)
echo "Analysis complete: $OUTPUT"
```

#### Advanced Command Patterns

**1. Interactive Commands:**
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

**2. File Generation Commands:**
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

**3. Workflow Automation Commands:**
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

#### Command Security & Permissions

**Permission Levels:**
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

**Secure Command Design:**
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

**Command Auditing:**
```bash
# Enable command audit logging
export OPENCODE_AUDIT_LOG=/var/log/opencode-commands.log

# View command history
!cat ~/.local/share/opencode/command-history.log

# Audit specific user/command
grep "user@example.com" /var/log/opencode-commands.log | grep "/deploy"
```

#### Command Performance Optimization

**Caching Commands:**
```bash
# Cache expensive command results
if [ ! -f /tmp/analysis-cache.json ]; then
  /analyze @src/ > /tmp/analysis-cache.json
fi
cat /tmp/analysis-cache.json
```

**Parallel Command Execution:**
```bash
# Run commands in parallel
/analyze @src/components/ &
/analyze @src/utils/ &
/analyze @src/api/ &
wait
echo "All analyses complete"
```

**Incremental Commands:**
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

#### Command Testing & Validation

**Unit Testing Commands:**
```bash
# Test command with sample input
/commands test analyze --input @test-data.json

# Test command output validation
/commands test deploy --expected "Deployment successful"

# Test command error handling
/commands test analyze --error "File not found"
```

**Integration Testing:**
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

**Performance Testing:**
```bash
# Benchmark command execution time
time opencode run "/analyze @src/"

# Profile command resource usage
/commands profile optimize --memory --cpu
```

#### Command Documentation

**Command Help System:**
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

**Auto-generated Documentation:**
```bash
# Generate command documentation
/commands docs --output docs/commands.md

# Update command help
/commands update-help

# Validate command documentation
/commands validate-docs
```

#### Command Ecosystem Management

**Command Registry:**
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

**Command Versioning:**
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

**Command Dependencies:**
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

#### Troubleshooting Commands

**Common Issues:**

1. **Command not found**
   ```bash
   # Check command location
   ls -la .opencode/commands/
   
   # Reload commands
   /commands reload
   
   # Check command permissions
   chmod +x .opencode/commands/command.sh
   ```

2. **Command execution failed**
   ```bash
   # Enable debug mode
   /commands run command-name --debug
   
   # Check command logs
   !cat ~/.local/share/opencode/command-debug.log
   
   # Test command manually
   !bash .opencode/commands/command.sh --test
   ```

3. **Permission errors**
   ```bash
   # Check command permissions
   /commands permissions command-name
   
   # Run with elevated permissions (careful!)
   /commands run command-name --sudo
   ```

4. **Command conflicts**
   ```bash
   # List conflicting commands
   /commands conflicts
   
   # Disable conflicting command
   /commands disable old-command
   ```

**Debug Commands:**
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

**Command Recovery:**
```bash
# Backup command configuration
/commands backup --output commands-backup.tar.gz

# Restore commands from backup
/commands restore commands-backup.tar.gz

# Reset commands to default
/commands reset --confirm
```

> **💡 Pro Tip**: Create a "command-tester" command that validates other commands. This helps maintain command quality and catch issues before they affect your workflow.

#### Best Practices for Command Design

**1. Keep Commands Focused:**
- One command, one responsibility
- Clear input/output expectations
- Minimal side effects

**2. Design for Composability:**
- Output that can be piped to other commands
- Standard exit codes and error messages
- Consistent argument parsing

**3. Prioritize Security:**
- Validate all inputs
- Use principle of least privilege
- Log command execution for audit

**4. Ensure Reliability:**
- Handle errors gracefully
- Provide clear error messages
- Include rollback mechanisms

**5. Optimize Performance:**
- Cache expensive operations
- Support incremental execution
- Provide progress feedback

**6. Maintain Documentation:**
- Clear usage examples
- Comprehensive help text
- Version compatibility notes

By following these best practices, you can create robust, reliable commands that enhance your OpenCode workflow without introducing complexity or security risks.

---

### Model Context Protocol (MCP) Servers

MCP (Model Context Protocol) servers extend OpenCode's capabilities by providing external tools and data sources. Think of MCP servers as "plugins for AI" that give OpenCode access to databases, APIs, file systems, and other external resources.

#### What are MCP Servers?

**MCP** is an open protocol that allows AI models to interact with external tools and data sources through a standardized interface.

**Key Concepts:**
1. **Servers**: External processes that provide tools/resources
2. **Tools**: Functions that the AI can call (read file, query DB, call API)
3. **Resources**: Data sources the AI can access (files, databases, APIs)
4. **Protocol**: Standardized communication between AI and servers

**Benefits of MCP:**
- **Extensibility**: Add new capabilities without modifying OpenCode
- **Security**: Isolate external access in separate processes
- **Standardization**: Consistent interface across different tools
- **Composability**: Combine multiple servers for complex workflows

#### Built-in MCP Servers

OpenCode includes several built-in MCP servers:

**File System Server:**
- **Purpose**: Read/write access to local files
- **Tools**: `read_file`, `write_file`, `list_directory`
- **Use Case**: Basic file operations within project

**Git Server:**
- **Purpose**: Version control operations
- **Tools**: `git_status`, `git_diff`, `git_commit`, `git_push`
- **Use Case**: Automated git workflows

**HTTP Server:**
- **Purpose**: Make HTTP requests
- **Tools**: `http_get`, `http_post`, `http_put`, `http_delete`
- **Use Case**: API integration, web scraping

**SQL Server:**
- **Purpose**: Database operations
- **Tools**: `sql_query`, `sql_execute`, `sql_schema`
- **Use Case**: Database management, data analysis

#### Installing MCP Servers

**Method 1: OpenCode Registry**
```bash
# List available MCP servers
/mcp list

# Install server from registry
/mcp install github

# Install specific version
/mcp install postgres --version 1.2.0
```

**Method 2: From URL**
```bash
# Install from GitHub repository
/mcp install https://github.com/user/mcp-server-repo

# Install from npm package
/mcp install npm:package-name

# Install from local file
/mcp install ./custom-mcp-server/
```

**Method 3: Manual Installation**
```bash
# Clone server repository
git clone https://github.com/modelcontextprotocol/servers.git

# Configure in OpenCode
echo '{
  "mcpServers": {
    "filesystem": {
      "command": "node",
      "args": ["servers/filesystem/dist/index.js"]
    }
  }
}' > ~/.config/opencode/opencode.json
```

#### Popular MCP Servers

**Development Servers:**

Server | Purpose | Tools
-------|---------|-------
**GitHub** | GitHub API access | `list_repos`, `create_pr`, `read_issue`
**PostgreSQL** | PostgreSQL database | `query`, `execute`, `schema`
**Redis** | Redis cache | `get`, `set`, `keys`, `del`
**Docker** | Container management | `ps`, `run`, `build`, `logs`
**AWS** | AWS services | `s3_list`, `ec2_describe`, `lambda_invoke`

**Productivity Servers:**

Server | Purpose | Tools
-------|---------|-------
**Google Calendar** | Calendar management | `list_events`, `create_event`, `update_event`
**Slack** | Slack integration | `send_message`, `read_channel`, `search_messages`
**Email** | Email management | `send_email`, `read_inbox`, `search_emails`
**Jira** | Issue tracking | `list_issues`, `create_issue`, `update_issue`

**Data & Analysis Servers:**

Server | Purpose | Tools
-------|---------|-------
**CSV** | CSV file operations | `read_csv`, `write_csv`, `filter_csv`
**JSON** | JSON manipulation | `parse_json`, `stringify_json`, `query_json`
**Excel** | Excel file operations | `read_excel`, `write_excel`, `format_excel`
**PDF** | PDF processing | `extract_text`, `merge_pdfs`, `create_pdf`

#### Using MCP Servers

**Basic Usage:**
```bash
# OpenCode automatically uses available MCP servers
# When you ask about files, it uses filesystem server
List all TypeScript files in the project

# When you mention git, it uses git server
What files have been modified recently?

# When you ask about APIs, it uses HTTP server
Fetch data from https://api.example.com/users
```

**Explicit Server Invocation:**
```bash
# Use specific server tools
Using the filesystem server, read @src/config.json

# Chain server operations
Using git server, check status, then using filesystem server, read changed files

# Combine multiple servers
Using github server, list issues, then using slack server, notify team
```

**Server Configuration:**
```json
// ~/.config/opencode/opencode.json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "your-token-here"
      }
    },
    "postgres": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-postgres"],
      "env": {
        "PGURI": "postgres://user:pass@localhost/db"
      }
    }
  }
}
```

#### Creating Custom MCP Servers

**Simple MCP Server Example (JavaScript):**
```javascript
// custom-server.js
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';

const server = new Server(
  {
    name: 'custom-server',
    version: '1.0.0',
  },
  {
    capabilities: {
      tools: {},
    },
  }
);

// Define a tool
server.setRequestHandler('tools/call', async (request) => {
  if (request.params.name === 'echo') {
    return {
      content: [
        {
          type: 'text',
          text: `Echo: ${request.params.arguments?.message || 'Hello!'}`,
        },
      ],
    };
  }
  
  throw new Error(`Unknown tool: ${request.params.name}`);
});

// Start server
const transport = new StdioServerTransport();
await server.connect(transport);
```

**Python MCP Server Example:**
```python
# custom_server.py
from mcp import Client, StdioServerParameters
import asyncio

async def main():
    # Create server
    server = Client(
        StdioServerParameters(
            command="python",
            args=["custom_server.py"],
        )
    )
    
    # Define tools
    @server.tool("echo")
    async def echo(message: str) -> str:
        return f"Echo: {message}"
    
    # Start server
    await server.initialize()
    
    # Run forever
    await asyncio.Future()

if __name__ == "__main__":
    asyncio.run(main())
```

**MCP Server Structure:**
```
mcp-server/
├── src/
│   ├── index.ts          # Main server file
│   ├── tools/            # Tool definitions
│   └── resources/        # Resource definitions
├── package.json          # Dependencies
├── tsconfig.json         # TypeScript config
└── README.md            # Documentation
```

#### Advanced MCP Patterns

**1. Server Composition:**
```bash
# Use multiple servers together
Using github server, get latest commit
Using filesystem server, read the changed files
Using http server, deploy to staging
Using slack server, notify deployment status
```

**2. Server Orchestration:**
```bash
# Conditional server usage
If there are database changes, use postgres server to run migrations
If there are API changes, use http server to test endpoints
If there are UI changes, use filesystem server to update snapshots
```

**3. Server Caching:**
```json
// Server with caching
{
  "mcpServers": {
    "github-cached": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-github"],
      "cache": {
        "enabled": true,
        "ttl": 300,  // 5 minutes
        "directory": "~/.cache/opencode/mcp"
      }
    }
  }
}
```

**4. Server Monitoring:**
```bash
# Monitor server performance
/mcp stats

# Check server health
/mcp health

# View server logs
/mcp logs github
```

#### MCP Server Security

**Authentication & Authorization:**
```json
// Secure server configuration
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "${env:GITHUB_TOKEN}"  // Use env variable
      },
      "permissions": {
        "network": true,
        "filesystem": false,
        "process": false
      }
    }
  }
}
```

**Server Sandboxing:**
```bash
# Run server in Docker container
/mcp install github --sandbox docker

# Use bubblewrap for isolation
/mcp install postgres --sandbox bubblewrap

# Custom sandbox configuration
/mcp install custom-server --sandbox-config ./sandbox.json
```

**Access Control:**
```yaml
# Server access control list
servers:
  github:
    allowed_tools:
      - list_repos
      - read_issues
      - create_pr
    denied_tools:
      - delete_repo
      - update_settings
    allowed_users:
      - developer@company.com
    rate_limit: 100/hour
```

#### MCP Server Development

**Development Workflow:**
1. **Plan**: Define server purpose and tools
2. **Develop**: Implement server with TypeScript/Python
3. **Test**: Test server with OpenCode
4. **Package**: Create distribution package
5. **Publish**: Share with community

**Testing MCP Servers:**
```bash
# Test server locally
/mcp test ./custom-server/

# Run server tests
cd mcp-server && npm test

# Integration test with OpenCode
opencode run "Test custom server: echo hello"
```

**Debugging MCP Servers:**
```bash
# Enable debug logging
export MCP_DEBUG=1

# View server communication
/mcp debug github

# Trace server execution
/mcp trace custom-server --output trace.json
```

#### MCP Server Ecosystem

**Community Servers:**
- **Official Registry**: https://github.com/modelcontextprotocol/servers
- **Community Contributions**: GitHub topics `mcp-server`
- **Enterprise Servers**: Internal company servers

**Server Standards:**
- **Naming**: Use descriptive names (github, postgres, slack)
- **Versioning**: Semantic versioning (1.0.0, 1.1.0, 2.0.0)
- **Documentation**: Include README with examples
- **Testing**: Include comprehensive test suite

**Server Distribution:**
```bash
# Publish to npm
npm publish --access public

# Publish to GitHub Packages
npm publish --registry=https://npm.pkg.github.com

# Create standalone binary
pkg dist/index.js --targets node18-linux-x64
```

#### Troubleshooting MCP Servers

**Common Issues:**

1. **Server not starting**
   ```bash
   # Check server command
   /mcp status github
   
   # View server logs
   /mcp logs github --tail 100
   
   # Test server manually
   !npx @modelcontextprotocol/server-github --help
   ```

2. **Tool not found**
   ```bash
   # List available tools
   /mcp tools github
   
   # Check tool permissions
   /mcp permissions github list_repos
   
   # Update server version
   /mcp update github
   ```

3. **Authentication errors**
   ```bash
   # Check environment variables
   /mcp env github
   
   # Re-authenticate
   /mcp auth github --reset
   
   # Use different auth method
   /mcp auth github --method oauth
   ```

4. **Performance issues**
   ```bash
   # Monitor server performance
   /mcp stats github --interval 5
   
   # Adjust server resources
   /mcp config github --memory 512mb --cpu 1
   
   # Enable caching
   /mcp config github --cache enabled
   ```

**Debug Commands:**
```bash
# Dry run server tool
/mcp tool github list_repos --dry-run

# Profile server performance
/mcp profile postgres query "SELECT * FROM users"

# Trace server communication
/mcp trace slack --output trace.json --verbose
```

**Server Recovery:**
```bash
# Backup server configuration
/mcp backup --output mcp-backup.tar.gz

# Restore servers from backup
/mcp restore mcp-backup.tar.gz

# Reset server to defaults
/mcp reset github --confirm
```

#### Best Practices for MCP Servers

**1. Design for Reliability:**
- Handle errors gracefully
- Implement retry logic
- Provide clear error messages
- Include timeout handling

**2. Prioritize Security:**
- Validate all inputs
- Implement rate limiting
- Use secure authentication
- Log security events

**3. Optimize Performance:**
- Implement caching
- Use connection pooling
- Batch operations when possible
- Monitor resource usage

**4. Ensure Compatibility:**
- Follow MCP specification
- Test with multiple OpenCode versions
- Provide migration guides
- Maintain backward compatibility

**5. Comprehensive Documentation:**
- Clear installation instructions
- Detailed tool documentation
- Usage examples
- Troubleshooting guide

**6. Community Engagement:**
- Accept feedback and issues
- Consider feature requests
- Participate in MCP community
- Share learnings and improvements

By leveraging MCP servers, you can extend OpenCode's capabilities far beyond its built-in features, creating a truly customized AI development environment tailored to your specific needs and workflows.

---

### FAQ & Troubleshooting

#### General Questions

**Q: Is OpenCode really free and open source?**
**A:** Yes! OpenCode is 100% open source under the MIT license. You can:
- View the source code: https://github.com/anomalyco/opencode
- Self-host the entire platform
- Modify and distribute your own version
- The only costs are for AI model usage (through Zen or other providers)

**Q: How does OpenCode compare to Claude Code?**
**A:** OpenCode offers several advantages:

Feature | OpenCode | Claude Code
--------|----------|------------
**Model Support** | 75+ providers | Claude only
**Pricing** | Pay-as-you-go | Monthly subscription
**Open Source** | ✅ Yes | ❌ No
**Self-hosting** | ✅ Yes | ❌ No
**Customization** | Extensive | Limited
**MCP Support** | ✅ Yes | Limited
**Local Models** | ✅ Yes | ❌ No

**Q: Can I use OpenCode without an internet connection?**
**A:** Partially. You need internet for:
- AI model inference (unless using local models)
- Installing/updating OpenCode
- MCP server communication

You can use OpenCode offline with:
- Local models (Ollama, llama.cpp)
- Cached responses
- Pre-installed MCP servers

#### Installation & Setup

**Q: OpenCode command not found after installation**
**A:** Try these solutions:
```bash
# 1. Check installation
which opencode

# 2. Add to PATH
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

# 3. Reinstall
curl -fsSL https://opencode.ai/install | bash

# 4. Check permissions
ls -la $(which opencode)
chmod +x $(which opencode)
```

**Q: Zen API key not working**
**A:** Common fixes:
1. **Regenerate key**: Visit opencode.ai/auth → API Keys → Regenerate
2. **Check billing**: Ensure payment method is added and active
3. **Verify format**: Key should be `zen_` followed by 64 characters
4. **Test connection**: `curl -H "Authorization: Bearer YOUR_KEY" https://api.opencode.ai/v1/models`

**Q: OpenCode crashes on startup**
**A:** Debug steps:
```bash
# Run with debug mode
opencode --debug

# Check system requirements
node --version  # Should be 18+
which git       # Git should be installed

# Clear corrupted config
rm -rf ~/.config/opencode
rm -rf ~/.opencode

# Try different terminal
# WezTerm or Alacritty recommended
```

#### Usage & Features

**Q: File references (@filename) not working**
**A:** Solutions:
```bash
# 1. Check current directory
!pwd

# 2. Use absolute path
@/full/path/to/file.ts

# 3. Check file exists
!ls -la @filename

# 4. Fuzzy search works best with unique names
# Instead of @config, use @config/database.ts
```

**Q: OpenCode making wrong changes**
**A:** Recovery options:
```bash
# 1. Undo changes
/undo  # Can run multiple times

# 2. Check git status
!git status

# 3. Restore from git
!git checkout -- .

# 4. Be more specific in prompts
# Instead of "fix the bug", use:
# "Fix the null pointer exception on line 45 in @src/utils/validation.ts"
```

**Q: Slow response times**
**A:** Performance optimization:
```bash
# 1. Use lighter model
/models
# Select smaller/faster model

# 2. Disable thinking steps
/thinking off

# 3. Use simpler theme
/themes
# Select "minimal" or "simple"

# 4. Reduce context size
/compact

# 5. Check system resources
!top -o cpu
```

#### Agents & Skills

**Q: Custom agent not appearing in list**
**A:** Fix agent configuration:
```bash
# 1. Check agent file location
ls -la ~/.config/opencode/agents/
ls -la .opencode/agents/

# 2. Verify file format
# Should be .md or .json
# Should have proper YAML frontmatter

# 3. Reload agents
/agents reload

# 4. Check permissions
chmod +r .opencode/agents/my-agent.md
```

**Q: Skill execution failing**
**A:** Debug skills:
```bash
# 1. Check skill syntax
/skills validate skill-name

# 2. Test with dry run
/skills run skill-name --dry-run

# 3. Check skill permissions
/skills permissions skill-name

# 4. View skill logs
!cat ~/.local/share/opencode/skills.log
```

**Q: Agent using wrong tools**
**A:** Configure tool permissions:
```markdown
# In agent configuration
## Tools
- read: true
- ask: true
- write: false  # Disable file writing
- edit: false   # Disable file editing
- bash: false   # Disable shell commands
- skill: ["review", "test"]  # Only specific skills
```

#### Models & Providers

**Q: Model not available in Zen**
**A:** Options:
1. **Check Zen status**: Visit status.opencode.ai
2. **Use alternative provider**: `/connect` → Add OpenAI/Anthropic directly
3. **Request model**: Contact OpenCode team via Discord
4. **Use similar model**: Try GPT 5.2 Codex instead of Claude Opus

**Q: High token usage/costs**
**A:** Cost optimization:
```bash
# 1. Monitor usage
!opencode stats

# 2. Use cheaper models
# Qwen 2.5 Coder instead of GPT 5.2 Codex
# MiniMax M2.5 Free for experimentation

# 3. Reduce context size
/compact "Keep only relevant parts"

# 4. Be concise in prompts
# Instead of long explanations, use:
# "Fix bug: @file.ts line 45"
```

**Q: Model giving poor quality responses**
**A:** Improve responses:
```bash
# 1. Adjust temperature
# Lower (0.1) for code, higher (0.7) for creative
/models --temperature 0.1

# 2. Provide more context
# Include relevant files, examples, constraints

# 3. Use chain of thought
# Ask model to think step by step

# 4. Try different model
# Some models better for specific tasks
```

#### Advanced Issues

**Q: MCP server connection failed**
**A:** Troubleshoot MCP:
```bash
# 1. Check server status
/mcp status

# 2. View server logs
/mcp logs server-name

# 3. Test server manually
!command-from-mcp-config --help

# 4. Reinstall server
/mcp reinstall server-name
```

**Q: OpenCode not recognizing project structure**
**A:** Improve project understanding:
```bash
# 1. Run /init
/init

# 2. Check AGENTS.md
cat AGENTS.md

# 3. Provide context manually
# "This is a React/TypeScript project using Tailwind CSS"

# 4. Share project structure
!find . -name "*.ts" -o -name "*.tsx" | head -20
```

**Q: Session sharing not working**
**A:** Fix sharing:
```bash
# 1. Check internet connection
!curl -I https://opencode.ai

# 2. Generate share link
/share

# 3. If private, check authentication
/connect status

# 4. Export manually
/export
# Then share the markdown file
```

#### Performance & Optimization

**Q: OpenCode using too much memory**
**A:** Memory optimization:
```bash
# 1. Reduce context window
export OPENCODE_MAX_CONTEXT=8000

# 2. Disable unused features
export OPENCODE_DISABLE_MCP=1
export OPENCODE_DISABLE_SKILLS=1

# 3. Use lighter models
/models
# Select models with smaller context

# 4. Regular cleanup
rm -rf ~/.cache/opencode
rm -rf ~/.local/share/opencode/sessions/old-*
```

**Q: Slow file operations**
**A:** File system optimization:
```bash
# 1. Exclude large directories
echo 'node_modules' > .opencodeignore
echo '.git' >> .opencodeignore
echo 'dist' >> .opencodeignore

# 2. Use SSD if possible
# OpenCode benefits from fast storage

# 3. Limit file scanning
export OPENCODE_FILE_SCAN_LIMIT=1000

# 4. Use specific file references
# Instead of @src/, use @src/utils/validation.ts
```

**Q: High CPU usage**
**A:** CPU optimization:
```bash
# 1. Check for background processes
!ps aux | grep opencode

# 2. Limit concurrent operations
export OPENCODE_MAX_CONCURRENT=2

# 3. Use simpler parsing
export OPENCODE_SIMPLE_PARSER=1

# 4. Update to latest version
curl -fsSL https://opencode.ai/install | bash
```

#### Security & Privacy

**Q: Is my code sent to AI providers?**
**A:** Yes, when using cloud-based models. For privacy:
1. **Use local models**: Ollama, llama.cpp
2. **Use enterprise providers**: Some offer data privacy guarantees
3. **Self-host OpenCode**: Complete control over data
4. **Review provider policies**: Check data handling terms

**Q: How to secure API keys?**
**A:** Best practices:
```bash
# 1. Use environment variables
export OPENCODE_API_KEY=your_key
export ZEN_API_KEY=your_zen_key

# 2. Never commit keys to git
echo '.env' >> .gitignore
echo '*.key' >> .gitignore

# 3. Use key rotation
# Rotate keys every 90 days

# 4. Monitor usage
!opencode stats --alert high-usage
```

**Q: Can OpenCode access sensitive files?**
**A:** Yes, by default. Restrict access:
```bash
# 1. Create .opencodeignore
echo '.env' > .opencodeignore
echo 'secrets/' >> .opencodeignore
echo '*.key' >> .opencodeignore

# 2. Use agent permissions
# Create "restricted" agent with limited tools

# 3. Run in isolated environment
docker run -it --rm -v $(pwd):/workspace ghcr.io/anomalyco/opencode

# 4. Audit file access
!find ~/.local/share/opencode -name "*.log" | xargs grep "access"
```

#### Community & Support

**Q: Where to get help?**
**A:** Support channels:
1. **Discord**: https://opencode.ai/discord (recommended)
2. **GitHub Issues**: https://github.com/anomalyco/opencode/issues
3. **Documentation**: https://opencode.ai/docs/
4. **Community Forum**: GitHub Discussions

**Q: How to contribute to OpenCode?**
**A:** Contribution options:
1. **Code**: Fork GitHub repo, submit PR
2. **Documentation**: Improve docs, add examples
3. **Skills/Agents**: Share with community
4. **MCP Servers**: Create and publish servers
5. **Bug Reports**: Submit detailed issues

**Q: Where to find examples and templates?**
**A:** Resources:
1. **This repository**: Examples in `examples/` directory
2. **Official examples**: https://github.com/anomalyco/opencode-examples
3. **Community templates**: GitHub topic `opencode-template`
4. **Skill registry**: Built-in `/skills list`

#### Updates & Migration

**Q: How to update OpenCode?**
**A:** Update methods:
```bash
# Using install script (recommended)
curl -fsSL https://opencode.ai/install | bash

# Using package manager
npm update -g opencode-ai
# or
brew upgrade opencode

# Check version
opencode --version
# Latest: https://github.com/anomalyco/opencode/releases
```

**Q: Breaking changes in new version**
**A:** Migration steps:
1. **Backup configuration**
   ```bash
   tar -czf opencode-backup.tar.gz ~/.config/opencode ~/.opencode
   ```
2. **Check changelog**: https://github.com/anomalyco/opencode/releases
3. **Test in isolated environment**
4. **Gradual migration**: Update one project at a time

**Q: Compatibility with other tools**
**A:** Integration status:
- **VS Code**: Extension available
- **JetBrains IDEs**: Plugin in development
- **Neovim**: Plugin available
- **Docker**: Official image available
- **CI/CD**: GitHub Actions available

Check https://opencode.ai/docs/ for latest integration status.

#### Common Error Messages

**Error: "No provider configured"**
```bash
# Solution:
/connect
# Follow prompts to add provider
```

**Error: "Model not available"**
```bash
# Solution:
/models
# Select available model
# or
/connect
# Add different provider
```

**Error: "Permission denied"**
```bash
# Solution:
# Check file permissions
!ls -la file.ts
# or
# Run with appropriate permissions
sudo chmod +r file.ts
```

**Error: "Out of context window"**
```bash
# Solution:
/compact
# or
# Be more concise
# or
# Use model with larger context
```

**Error: "Rate limited"**
```bash
# Solution:
# Wait and try again
# or
# Upgrade plan (Zen)
# or
# Use different provider
```

#### Pro Tips & Best Practices

**1. Start Simple:**
- Begin with basic commands
- Master Plan/Build mode switching
- Create simple agents before complex ones

**2. Iterate Gradually:**
- Small, testable changes
- Regular undo/redo
- Continuous refinement

**3. Document Everything:**
- Keep AGENTS.md updated
- Document custom skills/agents
- Share successful workflows

**4. Security First:**
- Regular key rotation
- Principle of least privilege
- Audit logs review

**5. Community Engagement:**
- Share learnings
- Contribute improvements
- Help others learn

**6. Continuous Learning:**
- Stay updated with new features
- Experiment with different models
- Adapt workflows as tools evolve

Remember: OpenCode is a powerful tool that gets better with practice. Start with simple tasks, build confidence, and gradually tackle more complex challenges. The community is here to help!


#### 1. Explore → Plan → Code → Commit

The most versatile workflow for complex problems:

**Explore:**
- Read relevant files, images, URLs
- Use subagents for verification
- Do **not** code yet - understand first

**Plan:**
- Ask OpenCode to create a plan
- Review and refine the approach
- Consider alternatives and trade-offs

**Code:**
- Implement the solution
- Verify reasonableness as you go
- Use tests to validate

**Commit:**
- Commit results with clear messages
- Create pull requests if needed
- Update documentation

**Example:**
```bash
# Explore: Understand the codebase
@explore Analyze @src/auth/ for authentication implementation

# Plan: Design the solution
[Plan] How would you add OAuth2 support to the existing authentication?

# Code: Implement
[Build] Implement OAuth2 support as planned

# Commit: Save changes
!git add .
!git commit -m "feat: Add OAuth2 authentication support"
```

#### 2. Test-Driven Development (TDD)

Ideal for changes verifiable with unit/integration tests:

**Write Tests:**
- Create tests based on expected behavior
- Mark as TDD to guide OpenCode
- Ensure tests fail initially (Red)

**Run & Fail Tests:**
- Confirm tests fail as expected
- No implementation yet

**Write Code:**
- Implement minimal code to pass tests (Green)
- Iterate with verification

**Refactor:**
- Improve code while keeping tests green
- Maintain test coverage

**Commit:**
- Final commit after all tests pass

**Example:**
```bash
# Start TDD session
/tdd "User registration validation"

# OpenCode guides through:
# 1. Write failing test
# 2. Implement minimal solution
# 3. Refactor
# 4. Repeat for each requirement

# Complete and commit
!git add .
!git commit -m "test: Add user registration validation"
```

#### 3. Visual Iteration

Perfect for UI/design work:

**Provide Visual Reference:**
- Drag and drop images into terminal
- Provide screenshots or mockups
- Describe desired outcome

**Implement Code:**
- Create code matching visual reference
- Take screenshots of result

**Iterate:**
- Compare result with reference
- Make adjustments
- Repeat until satisfied

**Commit:**
- Commit final implementation

**Example:**
```bash
# Drag dashboard-mockup.png into terminal
[Image #1: dashboard-mockup.png]

# Implement based on image
Create a React dashboard component matching [Image #1]

# Iterate based on results
The spacing looks off. Adjust to match the mockup more closely.

# Finalize
!git add .
!git commit -m "feat: Add dashboard component"
```

#### 4. Bug Fix Workflow

Systematic approach to debugging:

**Reproduce:**
- Understand the bug report
- Reproduce the issue
- Identify error conditions

**Diagnose:**
- Analyze logs and error messages
- Trace through code execution
- Identify root cause

**Fix:**
- Implement solution
- Test the fix
- Ensure no regressions

**Verify:**
- Run existing tests
- Add regression tests
- Confirm fix works

**Example:**
```bash
# Reproduce bug
The user reports: "Registration fails with invalid email error"

# Diagnose
@debugger Analyze @src/auth/registration.ts for email validation issues

# Fix
[Build] Fix the email validation regex in @src/auth/registration.ts

# Verify
!npm test -- --testPathPattern=registration
!git add .
!git commit -m "fix: Correct email validation regex"
```

#### 5. Feature Development Workflow

Complete feature implementation:

**Requirements Analysis:**
- Understand feature requirements
- Identify dependencies
- Plan implementation steps

**Architecture Design:**
- Design solution architecture
- Plan database schema (if needed)
- Design API endpoints

**Implementation:**
- Implement backend components
- Implement frontend components
- Connect pieces together

**Testing:**
- Write unit tests
- Write integration tests
- Perform user acceptance testing

**Deployment:**
- Prepare for deployment
- Update documentation
- Deploy to environment

**Example:**
```bash
# Multi-agent feature development
@product-manager Define requirements for user profile feature
@architect Design profile feature architecture
@backend Implement profile API endpoints
@frontend Implement profile UI components
@tester Create comprehensive test suite
@devops Prepare deployment configuration
@documentation Update user and developer docs
```

#### Workflow Customization

Create your own workflows by combining:

**Agent Chains:**
```bash
# Custom workflow using agent chain
@explore → @plan → @implement → @test → @review → @deploy
```

**Skill Sequences:**
```bash
# Custom workflow using skills
/analyze → /plan → /implement → /test → /review → /deploy
```

**Hybrid Approaches:**
```bash
# Mix agents and skills
@explore Analyze requirements
/plan Create implementation plan
@implement Write code
/test Run tests
/review Code review
/deploy Deploy changes
```

#### Workflow Automation

Automate repetitive workflows:

**Scheduled Tasks:**
```bash
# Daily code review
0 9 * * * opencode run "/review changed --since yesterday"

# Weekly dependency audit
0 10 * * 1 opencode run "/audit dependencies"

# Monthly performance analysis
0 11 1 * * opencode run "/analyze @src/ --focus performance"
```

**Event-Triggered Workflows:**
```bash
# On git push
git push && opencode run "/test && /review"

# On file change
inotifywait -m -e modify @src/ | while read; do
  opencode run "/analyze $REPLY"
done
```

**CI/CD Integration:**
```yaml
# GitHub Actions workflow
name: OpenCode Review
on: [pull_request]
jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: anomalyco/opencode-action@v1
        with:
          command: "/review changed"
          token: ${{ secrets.OPENCODE_TOKEN }}
```

#### Workflow Optimization

Measure and improve workflow efficiency:

**Metrics to Track:**
- Time from idea to implementation
- Bug rate per feature
- Test coverage changes
- Code review feedback quality
- Deployment frequency

**Optimization Strategies:**
1. **Identify bottlenecks**: Which steps take longest?
2. **Parallelize**: Can steps run concurrently?
3. **Automate**: Which manual steps can be automated?
4. **Simplify**: Can workflows be made simpler?
5. **Standardize**: Create templates for common workflows

**Continuous Improvement:**
```bash
# Regular workflow review
@analyzer Analyze our development workflow for improvements

# Implement improvements
[Build] Create workflow automation for repetitive tasks

# Measure impact
!opencode stats --workflow-metrics
```

By designing and optimizing your workflows, you can maximize OpenCode's potential and achieve consistent, high-quality results.



### Updates & References

#### Recent Updates (February 2026)

**✅ New Features:**
- **OpenCode Zen 2.0**: Enhanced model router with better pricing and more models
- **MCP Server Registry**: Centralized registry for community MCP servers
- **Team Workspaces**: Collaborative workspaces with shared billing and models
- **Advanced Agent Orchestration**: Improved multi-agent coordination

**🔄 Enhanced Features:**
- **TUI Performance**: 2x faster rendering and response times
- **Skill System**: More flexible skill creation and sharing
- **File Reference System**: Improved fuzzy matching and performance
- **Undo/Redo**: More reliable Git-based change management

**🔧 Improvements:**
- **Windows WSL Support**: Better integration and performance
- **Local Model Support**: Enhanced Ollama and llama.cpp integration
- **Security**: Improved authentication and permission systems
- **Documentation**: Comprehensive guides and examples

#### Version Compatibility

OpenCode Version | Minimum Requirements | Key Features
-----------------|---------------------|-------------
**1.5.x** | Node.js 18+, Git 2.30+ | Zen 2.0, MCP Registry, Team Workspaces
**1.4.x** | Node.js 18+, Git 2.30+ | Advanced Agents, Skills System
**1.3.x** | Node.js 16+, Git 2.25+ | MCP Support, Local Models
**1.2.x** | Node.js 16+, Git 2.25+ | Basic Agents, File References
**1.1.x** | Node.js 14+, Git 2.20+ | Core TUI, Basic Commands

#### Resources & References

**Official Resources:**
- **Website**: https://opencode.ai
- **Documentation**: https://opencode.ai/docs/
- **GitHub**: https://github.com/anomalyco/opencode
- **Discord**: https://opencode.ai/discord
- **Status**: https://status.opencode.ai

**Community Resources:**
- **Awesome OpenCode**: https://github.com/awesome-opencode/awesome-opencode
- **OpenCode Examples**: https://github.com/anomalyco/opencode-examples
- **MCP Server Registry**: https://github.com/modelcontextprotocol/servers
- **Skill Templates**: https://github.com/opencode-skills/templates

**Learning Resources:**
- **Tutorials**: https://opencode.ai/learn
- **Video Guides**: YouTube channel "OpenCode AI"
- **Blog**: https://opencode.ai/blog
- **Community Forum**: GitHub Discussions

**Integration Guides:**
- **VS Code Extension**: https://marketplace.visualstudio.com/items?itemName=opencode.opencode-vscode
- **Neovim Plugin**: https://github.com/opencode/opencode.nvim
- **Docker Images**: https://hub.docker.com/r/opencode/opencode
- **GitHub Action**: https://github.com/marketplace/actions/opencode

#### Contributing

**Ways to Contribute:**
1. **Code Contributions**: Fork and submit PRs
2. **Documentation**: Improve docs and add examples
3. **Bug Reports**: Submit detailed issues
4. **Feature Requests**: Suggest new features
5. **Community Help**: Answer questions on Discord

**Contribution Guidelines:**
```bash
# 1. Fork repository
# 2. Create feature branch
git checkout -b feature/amazing-feature

# 3. Make changes and test
npm test

# 4. Commit changes
git commit -m "Add amazing feature"

# 5. Push to branch
git push origin feature/amazing-feature

# 6. Create Pull Request
```

**Development Setup:**
```bash
# Clone repository
git clone https://github.com/anomalyco/opencode.git
cd opencode

# Install dependencies
npm install

# Build project
npm run build

# Run tests
npm test

# Start development server
npm run dev
```

#### License

This repository is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

OpenCode itself is also MIT licensed. You are free to:
- Use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
- Use for commercial purposes
- Use for private purposes
- Modify and distribute your modifications

The only requirement is to include the original copyright notice and license.

#### Acknowledgments

**OpenCode Team:**
- **Dax** - Founder and lead developer
- **Adam** - Core contributor and infrastructure
- **Community Contributors** - Everyone who has submitted PRs, issues, or helped others

**Special Thanks:**
- **Anthropic** for Claude models and inspiration
- **OpenAI** for GPT models and API
- **Google** for Gemini models
- **All model providers** in the Zen network
- **MCP Community** for server contributions
- **Every user** who has provided feedback and suggestions

**Inspiration:**
- Claude Code for showing the potential of terminal-based AI coding
- GitHub Copilot for pioneering AI pair programming
- Cursor for advancing AI-assisted development
- All open source AI projects pushing the boundaries

#### Support & Feedback

**Getting Help:**
1. **Check FAQ** above for common issues
2. **Search Documentation**: https://opencode.ai/docs/
3. **Ask on Discord**: https://opencode.ai/discord (fastest response)
4. **GitHub Issues**: https://github.com/anomalyco/opencode/issues

**Providing Feedback:**
- **Feature Requests**: GitHub Discussions
- **Bug Reports**: GitHub Issues with detailed reproduction steps
- **Success Stories**: Share on Discord or Twitter (#OpenCodeAI)
- **Improvement Suggestions**: All channels welcome

**Enterprise Support:**
- **Email**: enterprise@opencode.ai
- **Website**: https://opencode.ai/enterprise
- **Slack**: Private Slack channel available

#### Stay Updated

**Newsletter:**
- Subscribe at https://opencode.ai/newsletter
- Monthly updates on new features and improvements
- Tips and tricks for advanced usage
- Community highlights and success stories

**Social Media:**
- **Twitter**: @OpenCodeAI
- **LinkedIn**: OpenCode AI
- **YouTube**: OpenCode AI
- **GitHub**: anomalyco/opencode

**RSS Feed:**
- Blog: https://opencode.ai/blog/feed.xml
- Releases: https://github.com/anomalyco/opencode/releases.atom

---

### Final Thoughts

OpenCode represents a new paradigm in AI-assisted development: open, flexible, and powerful. By combining multi-model support with extensive customization and a vibrant ecosystem, it empowers developers to work smarter, not harder.

**Key Takeaways:**
1. **Start Simple**: Master the basics before diving into advanced features
2. **Iterate Gradually**: Small, consistent improvements beat massive overhauls
3. **Customize Thoughtfully**: Build workflows that match your specific needs
4. **Engage with Community**: Share learnings and learn from others
5. **Focus on Value**: Use OpenCode to solve real problems, not just as a novelty

**The Future of OpenCode:**
The roadmap includes:
- **Enhanced collaboration tools**
- **More intelligent agent orchestration**
- **Expanded MCP ecosystem**
- **Improved local model support**
- **Enterprise-grade features**

**Your Journey Starts Now:**
```bash
# Install OpenCode
curl -fsSL https://opencode.ai/install | bash

# Start your first project
cd /path/to/project
opencode
/init

# Begin exploring
Hello OpenCode! What can you help me build today?
```

Welcome to the future of AI-assisted development. Happy coding!

---

*This guide is maintained by the OpenCode community. Last updated: February 2026*

[![OpenCode](https://img.shields.io/badge/OpenCode-Everything%20You%20Need%20to%20Know-blue)](https://opencode.ai)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Discord](https://img.shields.io/discord/123456789012345678?label=Discord&logo=discord&logoColor=white)](https://opencode.ai/discord)
[![GitHub Stars](https://img.shields.io/github/stars/anomalyco/opencode?style=social)](https://github.com/anomalyco/opencode)