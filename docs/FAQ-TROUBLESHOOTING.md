# FAQ & Troubleshooting Guide

## ❓ General Questions

### Q: Is OpenCode really free and open source?
**A:** Yes! OpenCode is 100% open source under the MIT license. You can:
- View the source code: https://github.com/anomalyco/opencode
- Self-host the entire platform
- Modify and distribute your own version
- The only costs are for AI model usage (through Zen or other providers)

### Q: How does OpenCode compare to Claude Code?
**A:** OpenCode offers several advantages:

| Feature | OpenCode | Claude Code |
|---------|----------|-------------|
| **Model Support** | 75+ providers | Claude only |
| **Pricing** | Pay-as-you-go | Monthly subscription |
| **Open Source** | ✅ Yes | ❌ No |
| **Self-hosting** | ✅ Yes | ❌ No |
| **Customization** | Extensive | Limited |
| **MCP Support** | ✅ Yes | Limited |
| **Local Models** | ✅ Yes | ❌ No |

### Q: Can I use OpenCode without an internet connection?
**A:** Partially. You need internet for:
- AI model inference (unless using local models)
- Installing/updating OpenCode
- MCP server communication

You can use OpenCode offline with:
- Local models (Ollama, llama.cpp)
- Cached responses
- Pre-installed MCP servers

## 🛠️ Installation & Setup

### Q: OpenCode command not found after installation
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

### Q: Zen API key not working
**A:** Common fixes:
1. **Regenerate key**: Visit opencode.ai/auth → API Keys → Regenerate
2. **Check billing**: Ensure payment method is added and active
3. **Verify format**: Key should be `zen_` followed by 64 characters
4. **Test connection**: `curl -H "Authorization: Bearer YOUR_KEY" https://api.opencode.ai/v1/models`

### Q: OpenCode crashes on startup
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

## 🚀 Usage & Features

### Q: File references (@filename) not working
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

### Q: OpenCode making wrong changes
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

### Q: Slow response times
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

## 🤖 Agents & Skills

### Q: Custom agent not appearing in list
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

### Q: Skill execution failing
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

### Q: Agent using wrong tools
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

## 🧠 Models & Providers

### Q: Model not available in Zen
**A:** Options:
1. **Check Zen status**: Visit status.opencode.ai
2. **Use alternative provider**: `/connect` → Add OpenAI/Anthropic directly
3. **Request model**: Contact OpenCode team via Discord
4. **Use similar model**: Try GPT 5.2 Codex instead of Claude Opus

### Q: High token usage/costs
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

### Q: Model giving poor quality responses
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

## ⚡ Advanced Issues

### Q: MCP server connection failed
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

### Q: OpenCode not recognizing project structure
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

### Q: Session sharing not working
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

## ⚡ Performance & Optimization

### Q: OpenCode using too much memory
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

### Q: Slow file operations
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

### Q: High CPU usage
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

## 🔒 Security & Privacy

### Q: Is my code sent to AI providers?
**A:** Yes, when using cloud-based models. For privacy:
1. **Use local models**: Ollama, llama.cpp
2. **Use enterprise providers**: Some offer data privacy guarantees
3. **Self-host OpenCode**: Complete control over data
4. **Review provider policies**: Check data handling terms

### Q: How to secure API keys?
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

### Q: Can OpenCode access sensitive files?
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

## 🤝 Community & Support

### Q: Where to get help?
**A:** Support channels:
1. **Discord**: https://opencode.ai/discord (recommended)
2. **GitHub Issues**: https://github.com/anomalyco/opencode/issues
3. **Documentation**: https://opencode.ai/docs/
4. **Community Forum**: GitHub Discussions

### Q: How to contribute to OpenCode?
**A:** Contribution options:
1. **Code**: Fork GitHub repo, submit PRs
2. **Documentation**: Improve docs, add examples
3. **Skills/Agents**: Share with community
4. **MCP Servers**: Create and publish servers
5. **Bug Reports**: Submit detailed issues

### Q: Where to find examples and templates?
**A:** Resources:
1. **This repository**: Examples in `examples/` directory
2. **Official examples**: https://github.com/anomalyco/opencode-examples
3. **Community templates**: GitHub topic `opencode-template`
4. **Skill registry**: Built-in `/skills list`

## 🔄 Updates & Migration

### Q: How to update OpenCode?
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

### Q: Breaking changes in new version
**A:** Migration steps:
1. **Backup configuration**
   ```bash
   tar -czf opencode-backup.tar.gz ~/.config/opencode ~/.opencode
   ```
2. **Check changelog**: https://github.com/anomalyco/opencode/releases
3. **Test in isolated environment**
4. **Gradual migration**: Update one project at a time

### Q: Compatibility with other tools
**A:** Integration status:
- **VS Code**: Extension available
- **JetBrains IDEs**: Plugin in development
- **Neovim**: Plugin available
- **Docker**: Official image available
- **CI/CD**: GitHub Actions available

Check https://opencode.ai/docs/ for latest integration status.

## 🚨 Common Error Messages

### Error: "No provider configured"
```bash
# Solution:
/connect
# Follow prompts to add provider
```

### Error: "Model not available"
```bash
# Solution:
/models
# Select available model
# or
/connect
# Add different provider
```

### Error: "Permission denied"
```bash
# Solution:
# Check file permissions
!ls -la file.ts
# or
# Run with appropriate permissions
sudo chmod +r file.ts
```

### Error: "Out of context window"
```bash
# Solution:
/compact
# or
# Be more concise
# or
# Use model with larger context
```

### Error: "Rate limited"
```bash
# Solution:
# Wait and try again
# or
# Upgrade plan (Zen)
# or
# Use different provider
```

## 💡 Pro Tips & Best Practices

### 1. Start Simple:
- Begin with basic commands
- Master Plan/Build mode switching
- Create simple agents before complex ones

### 2. Iterate Gradually:
- Small, testable changes
- Regular undo/redo
- Continuous refinement

### 3. Document Everything:
- Keep AGENTS.md updated
- Document custom skills/agents
- Share successful workflows

### 4. Security First:
- Regular key rotation
- Principle of least privilege
- Audit logs review

### 5. Community Engagement:
- Share learnings
- Contribute improvements
- Help others learn

### 6. Continuous Learning:
- Stay updated with new features
- Experiment with different models
- Adapt workflows as tools evolve

Remember: OpenCode is a powerful tool that gets better with practice. Start with simple tasks, build confidence, and gradually tackle more complex challenges. The community is here to help!

---

## 📚 Additional Resources

### Quick Reference:
- [Main Guide](../README.md) - Overview and quick start
- [Quick Start Guide](QUICKSTART.md) - Installation and setup
- [Zen Guide](ZEN-GUIDE.md) - Model router details
- [TUI Guide](TUI-MASTERY.md) - Terminal interface mastery
- [Agents Guide](AGENTS-GUIDE.md) - AI agents comprehensive guide
- [Skills Guide](SKILLS-GUIDE.md) - Skills system
- [Commands Reference](COMMANDS-REFERENCE.md) - Complete command list
- [MCP Guide](MCP-GUIDE.md) - MCP servers
- [Workflows Guide](WORKFLOWS.md) - Development workflows

### Official Links:
- **Website**: https://opencode.ai
- **Documentation**: https://opencode.ai/docs/
- **GitHub**: https://github.com/anomalyco/opencode
- **Discord**: https://opencode.ai/discord
- **Status**: https://status.opencode.ai

---

*Last updated: February 2026*