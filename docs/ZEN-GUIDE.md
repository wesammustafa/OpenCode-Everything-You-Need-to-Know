# Zen Model Router Guide

## 🎯 What is Zen?
**OpenCode Zen** is a curated model gateway that provides verified, optimized AI models specifically for coding tasks with pay-as-you-go pricing.

### Key Benefits:
- **Verified Models**: Tested and benchmarked for coding
- **Cost Transparency**: Pay per token, no monthly subscriptions
- **No Lock-in**: Works alongside other providers
- **Team Features**: Workspace management, centralized billing
- **BYOK Support**: Bring your own OpenAI/Anthropic keys

## 📊 Key Specifications

| Feature | Specification |
|---------|---------------|
| **Model Support** | 75+ providers via AI SDK |
| **Pricing Model** | Pay-as-you-go per token |
| **Free Models** | MiniMax M2.5 Free, Big Pickle (beta) |
| **Cost Example** | GPT 5.2 Codex: $1.75/1M input, $14/1M output |
| **Team Features** | Workspace management, centralized billing |
| **BYOK Support** | ✅ Yes (bring your own keys) |

## 🚀 How Zen Works

### Step-by-Step Setup:

1. **Sign Up**: Visit [opencode.ai/auth](https://opencode.ai/auth)
2. **Add Billing**: Add credit card for pay-as-you-go usage
3. **Get API Key**: Copy your unique Zen API key
4. **Configure in OpenCode**:
   ```bash
   opencode
   /connect
   # Select "opencode" and paste your key
   ```
5. **Select Models**: Use `/models` to see available curated models

## 💰 Available Models & Pricing

| Model | Input Cost | Output Cost | Best For |
|-------|------------|-------------|----------|
| **GPT 5.2 Codex** | $1.75/1M | $14/1M | General coding, complex tasks |
| **Claude Sonnet 4.6** | $3-6/1M | $15-22.50/1M | Reasoning, analysis |
| **Gemini 2.5 Pro** | $2.50/1M | $10/1M | Multimodal tasks |
| **Qwen 2.5 Coder** | $0.50/1M | $2/1M | Budget coding, simple tasks |
| **MiniMax M2.5 Free** | Free | Free | Learning, experimentation |

## 🤔 Zen vs Direct Providers

### ✅ Use Zen When:
- You want curated, optimized models for coding
- You prefer pay-as-you-go over monthly subscriptions
- You need access to multiple providers with one API key
- You want the latest models without manual configuration
- You're new to AI coding and want a guided experience

### 🔧 Use Direct Providers When:
- You already have existing API credits
- You need specific model versions not in Zen
- You have enterprise agreements with specific providers
- You're using local/self-hosted models

## 💸 Cost Comparison

| Tool | Pricing Model | Monthly Cost (Avg) | Model Flexibility |
|------|---------------|-------------------|------------------|
| **OpenCode Zen** | Pay-as-you-go | $5-50 (based on usage) | 75+ models |
| **Claude Code Pro** | Subscription | $20/month | Claude only |
| **Cursor Pro** | Subscription | $20/month | Limited selection |
| **GitHub Copilot** | Subscription | $10/month | GitHub models only |

> **💡 Pro Tip**: Start with Zen's free models (MiniMax M2.5 Free) to learn OpenCode, then upgrade to paid models as needed.

## 🛠️ Advanced Zen Features

### 1. Model Switching
```bash
# Switch between models on the fly
/models
# Select from the list using arrow keys
```

### 2. Usage Monitoring
```bash
# Check your token usage
!opencode stats
# or in TUI, costs are shown in real-time
```

### 3. Team Workspaces
- Create team workspaces for shared billing
- Set monthly usage limits per team member
- Centralized model curation for consistency

### 4. BYOK (Bring Your Own Key)
- Use your existing OpenAI/Anthropic keys
- Still access Zen's curated models
- Unified billing and management

## 🚨 Troubleshooting Zen

### Common Issues:

**1. "Invalid API key"**
- Regenerate key at [opencode.ai/auth](https://opencode.ai/auth)

**2. "No models available"**
- Check billing status, may need to add payment method

**3. "Rate limited"**
- Upgrade plan or wait for reset

**4. "Model not responding"**
- Try alternative model or check provider status

### Debug Commands:
```bash
# Check connection status
!opencode models --provider opencode

# Test API key
curl -H "Authorization: Bearer YOUR_API_KEY" https://api.opencode.ai/v1/models
```

> **🚨 SECURITY NOTE**: Never commit your Zen API key to version control. Use environment variables or OpenCode's secure credential storage.

## 📊 Zen vs Traditional Subscriptions

### Traditional Model (Claude Code, Cursor):
- Monthly subscription ($20/month)
- Limited to specific models
- Pay even if you don't use it
- Vendor lock-in

### Zen Model:
- Pay per token used
- Access to 75+ models
- No monthly commitment
- Mix and match providers
- Transparent pricing

### Example Cost Calculation:
- 100,000 tokens input + 50,000 tokens output
- Using GPT 5.2 Codex: (0.1 * $1.75) + (0.05 * $14) = $0.175 + $0.70 = $0.875
- Same usage on Claude Code: $20/month (minimum)

> **📊 Real-World Usage**: Most developers spend $5-20/month with Zen, significantly less than fixed subscriptions, while getting access to better models.

## 🎯 Best Practices

1. **Start Free**: Begin with MiniMax M2.5 Free to learn
2. **Monitor Usage**: Use `!opencode stats` regularly
3. **Choose Wisely**: Match model to task (coding vs analysis)
4. **Set Limits**: Use team workspace limits for cost control
5. **Stay Updated**: New models added regularly

## 🔗 Related Resources

- [OpenCode Website](https://opencode.ai)
- [Zen Dashboard](https://opencode.ai/auth)
- [Model Status](https://status.opencode.ai)
- [Community Discord](https://opencode.ai/discord)

---

## 📚 What's Next?

- [TUI Mastery Guide](TUI-MASTERY.md) - Master the terminal interface
- [Agents Guide](AGENTS-GUIDE.md) - Work with AI agents
- [Skills Guide](SKILLS-GUIDE.md) - Create reusable workflows
- [Back to Main Guide](../README.md)

---

*Last updated: February 2026*