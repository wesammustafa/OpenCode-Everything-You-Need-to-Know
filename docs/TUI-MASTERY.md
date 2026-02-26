# TUI Mastery Guide

## 🎯 Overview
OpenCode's Terminal User Interface (TUI) is where the magic happens. This guide covers everything you need to master the TUI for maximum productivity.

## 🖥️ TUI Layout Overview

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

## ⌨️ Essential Keyboard Shortcuts

| Shortcut | Action | Description |
|----------|--------|-------------|
| **Tab** | Switch agents | Toggle between Build and Plan modes |
| **Ctrl+C** | Exit | Exit OpenCode (press twice to force) |
| **Ctrl+R** | Redo | Redo last undone change |
| **Ctrl+U** | Undo | Undo last change |
| **Ctrl+L** | Clear | Clear terminal screen |
| **Ctrl+K** | Search | Search command history |
| **↑/↓** | History | Navigate command history |
| **@** | File search | Fuzzy search for project files |
| **!** | Shell prefix | Execute shell command |
| **/** | Command mode | Enter slash command mode |
| **Esc** | Cancel | Cancel current operation |

## 📁 File Reference System (@ Syntax)

OpenCode's `@` syntax revolutionizes how you reference files:

### Basic File Reference:
```bash
# Reference a specific file
Can you explain the authentication logic in @src/auth/index.ts?

# Fuzzy search - OpenCode will help you find the file
I need to update the configuration in @config
```

### Multiple File References:
```bash
# Compare two files
Compare the implementation in @src/old-impl.ts and @src/new-impl.ts

# Analyze entire directory
What's the structure of @src/components/?
```

### Line-Specific References:
```bash
# Reference specific lines
Check lines 45-60 in @src/utils/validation.ts

# Error location
There's an error on line 123 in @src/api/server.ts
```

## 💻 Shell Command Integration

Execute shell commands directly within OpenCode:

### Basic Shell Commands:
```bash
# Run any shell command with ! prefix
!ls -la
!git status
!npm install
!docker ps
```

### Command Output in Context:
```bash
# Use command output in your prompt
!pwd
# OpenCode sees: "/Users/you/project"

Now create a new directory here called "tests"
```

### Chaining Commands:
```bash
# Multiple commands
!git status && !git diff

# Capture output for analysis
!cat package.json | grep version
What version of React are we using based on the output above?
```

## 🖼️ Image Analysis

OpenCode can analyze images dragged into the terminal:

### Using Images:
1. **Drag and drop** any image file into the terminal
2. OpenCode automatically adds it to the prompt
3. Reference the image in your queries

### Example Workflow:
```bash
# 1. Drag UI mockup into terminal
# 2. OpenCode detects: [Image #1: dashboard-mockup.png]

Create a React component that matches this design [Image #1]
```

### Supported Image Types:
- PNG, JPEG, GIF, WebP
- Screenshots, mockups, diagrams
- UI designs, architecture diagrams

## 🔄 Agent Switching (Build vs Plan)

OpenCode's dual-agent system is its secret weapon:

### Plan Mode (Read-Only):
- **Activate**: Press `Tab` (shows `[Plan]` in status bar)
- **Purpose**: Analyze, plan, brainstorm without making changes
- **Use Case**: "How would you implement this feature?"

### Build Mode (Read-Write):
- **Activate**: Press `Tab` (shows `[Build]` in status bar)
- **Purpose**: Make actual code changes
- **Use Case**: "Go ahead and implement the plan"

### Workflow Example:
```bash
# Start in Plan mode (default)
[Plan] How would you add dark mode to this React app?

# Review the plan, ask questions
What about CSS variables vs Tailwind?

# Switch to Build mode (Tab)
[Build] Sounds good! Implement it.
```

## 💬 Conversation Management

### Session Persistence:
- Conversations are automatically saved
- Resume where you left off
- Git-based undo/redo system

### Multiple Sessions:
```bash
# List sessions
/sessions

# Switch sessions
/sessions switch session-name

# Delete session
/sessions delete old-session
```

### Export Conversations:
```bash
# Export to markdown
/export

# Creates: opencode-conversation-2025-02-26.md
```

## ⚡ Advanced TUI Features

### 1. Compact Mode:
```bash
# Summarize long conversations
/compact

# Focus on specific topics
/compact "Focus on the authentication changes"
```

### 2. Editor Integration:
```bash
# Open external editor for long messages
/editor

# Uses $EDITOR environment variable
```

### 3. Theme Customization:
```bash
# Change TUI theme
/themes

# Select from available themes
# Popular: catppuccin, dracula, nord, solarized
```

### 4. Real-time Cost Display:
- Token usage shown in status bar
- Cost estimates for current session
- Provider-specific pricing

## 🚀 Productivity Tips

### 1. Quick File Navigation:
```bash
# Use @ with partial names
@utils  # Finds utils/ directory or utils.ts
@.env   # Finds .env files
@test   # Finds test files
```

### 2. Command History:
- Press `↑` to cycle through previous commands
- `Ctrl+K` to search history
- History persists across sessions

### 3. Multi-line Input:
```bash
# Shift+Enter for new lines
This is a multi-line
query that spans
multiple lines
```

### 4. Quick Provider Switching:
```bash
# Change model on the fly
/models

# Select from list
# Changes apply immediately
```

## 🛠️ Troubleshooting TUI Issues

### Common Issues:

**1. TUI not rendering properly**
```bash
# Check terminal compatibility
echo $TERM

# Try different terminal emulator
# WezTerm or Alacritty recommended
```

**2. Input lag or slow response**
```bash
# Check system resources
!top

# Try lighter model
/models
# Select smaller model
```

**3. Images not working**
```bash
# Check terminal image support
# Use WezTerm for best image support

# Alternative: describe image in text
```

**4. File references not found**
```bash
# Check current directory
!pwd

# Use absolute paths if needed
@/full/path/to/file.ts
```

### Performance Optimization:
```bash
# Use lighter themes
/themes
# Select "minimal" or "simple"

# Disable thinking steps
/thinking off

# Reduce verbosity in agent settings
```

## 🎨 TUI Customization

### Keybind Customization:
```json
// ~/.config/opencode/keybinds.json
{
  "switch_agent": "Tab",
  "exit": ["Ctrl+C", "Ctrl+D"],
  "clear": "Ctrl+L",
  "history_search": "Ctrl+K"
}
```

### Theme Configuration:
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

### Status Bar Customization:
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

## 🎯 Mastery Checklist

- [ ] Can switch between Plan and Build modes with Tab
- [ ] Know how to reference files with @ syntax
- [ ] Can execute shell commands with ! prefix
- [ ] Understand how to use image analysis
- [ ] Know essential keyboard shortcuts
- [ ] Can manage conversations and sessions
- [ ] Know how to troubleshoot common issues
- [ ] Have customized TUI to personal preferences

> **💡 Pro Tip**: Master the `Tab` key switching between Plan and Build modes. This single habit will dramatically improve your OpenCode workflow efficiency.

---

## 📚 What's Next?

- [Agents Guide](AGENTS-GUIDE.md) - Work with AI agents
- [Skills Guide](SKILLS-GUIDE.md) - Create reusable workflows
- [Workflows Guide](WORKFLOWS.md) - Design development workflows
- [Back to Main Guide](../README.md)

---

*Last updated: February 2026*