# MCP (Model Context Protocol) Servers Guide

## 🎯 What are MCP Servers?
**MCP** (Model Context Protocol) servers extend OpenCode's capabilities by providing external tools and data sources. Think of MCP servers as "plugins for AI" that give OpenCode access to databases, APIs, file systems, and other external resources.

### Key Concepts:
1. **Servers**: External processes that provide tools/resources
2. **Tools**: Functions that the AI can call (read file, query DB, call API)
3. **Resources**: Data sources the AI can access (files, databases, APIs)
4. **Protocol**: Standardized communication between AI and servers

### Benefits of MCP:
- **Extensibility**: Add new capabilities without modifying OpenCode
- **Security**: Isolate external access in separate processes
- **Standardization**: Consistent interface across different tools
- **Composability**: Combine multiple servers for complex workflows

## 🤖 Built-in MCP Servers

### File System Server:
- **Purpose**: Read/write access to local files
- **Tools**: `read_file`, `write_file`, `list_directory`
- **Use Case**: Basic file operations within project

### Git Server:
- **Purpose**: Version control operations
- **Tools**: `git_status`, `git_diff`, `git_commit`, `git_push`
- **Use Case**: Automated git workflows

### HTTP Server:
- **Purpose**: Make HTTP requests
- **Tools**: `http_get`, `http_post`, `http_put`, `http_delete`
- **Use Case**: API integration, web scraping

### SQL Server:
- **Purpose**: Database operations
- **Tools**: `sql_query`, `sql_execute`, `sql_schema`
- **Use Case**: Database management, data analysis

## 📦 Installing MCP Servers

### Method 1: OpenCode Registry
```bash
# List available MCP servers
/mcp list

# Install server from registry
/mcp install github

# Install specific version
/mcp install postgres --version 1.2.0
```

### Method 2: From URL
```bash
# Install from GitHub repository
/mcp install https://github.com/user/mcp-server-repo

# Install from npm package
/mcp install npm:package-name

# Install from local file
/mcp install ./custom-mcp-server/
```

### Method 3: Manual Installation
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

## 📋 Popular MCP Servers

### Development Servers:

| Server | Purpose | Tools |
|--------|---------|-------|
| **GitHub** | GitHub API access | `list_repos`, `create_pr`, `read_issue` |
| **PostgreSQL** | PostgreSQL database | `query`, `execute`, `schema` |
| **Redis** | Redis cache | `get`, `set`, `keys`, `del` |
| **Docker** | Container management | `ps`, `run`, `build`, `logs` |
| **AWS** | AWS services | `s3_list`, `ec2_describe`, `lambda_invoke` |

### Productivity Servers:

| Server | Purpose | Tools |
|--------|---------|-------|
| **Google Calendar** | Calendar management | `list_events`, `create_event`, `update_event` |
| **Slack** | Slack integration | `send_message`, `read_channel`, `search_messages` |
| **Email** | Email management | `send_email`, `read_inbox`, `search_emails` |
| **Jira** | Issue tracking | `list_issues`, `create_issue`, `update_issue` |

### Data & Analysis Servers:

| Server | Purpose | Tools |
|--------|---------|-------|
| **CSV** | CSV file operations | `read_csv`, `write_csv`, `filter_csv` |
| **JSON** | JSON manipulation | `parse_json`, `stringify_json`, `query_json` |
| **Excel** | Excel file operations | `read_excel`, `write_excel`, `format_excel` |
| **PDF** | PDF processing | `extract_text`, `merge_pdfs`, `create_pdf` |

## 🚀 Using MCP Servers

### Basic Usage:
```bash
# OpenCode automatically uses available MCP servers
# When you ask about files, it uses filesystem server
List all TypeScript files in the project

# When you mention git, it uses git server
What files have been modified recently?

# When you ask about APIs, it uses HTTP server
Fetch data from https://api.example.com/users
```

### Explicit Server Invocation:
```bash
# Use specific server tools
Using the filesystem server, read @src/config.json

# Chain server operations
Using git server, check status, then using filesystem server, read changed files

# Combine multiple servers
Using github server, list issues, then using slack server, notify team
```

### Server Configuration:
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

## 🛠️ Creating Custom MCP Servers

### Simple MCP Server Example (JavaScript):
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

### Python MCP Server Example:
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

### MCP Server Structure:
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

## 🔗 Advanced MCP Patterns

### 1. Server Composition:
```bash
# Use multiple servers together
Using github server, get latest commit
Using filesystem server, read the changed files
Using http server, deploy to staging
Using slack server, notify deployment status
```

### 2. Server Orchestration:
```bash
# Conditional server usage
If there are database changes, use postgres server to run migrations
If there are API changes, use http server to test endpoints
If there are UI changes, use filesystem server to update snapshots
```

### 3. Server Caching:
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

### 4. Server Monitoring:
```bash
# Monitor server performance
/mcp stats

# Check server health
/mcp health

# View server logs
/mcp logs github
```

## 🔒 MCP Server Security

### Authentication & Authorization:
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

### Server Sandboxing:
```bash
# Run server in Docker container
/mcp install github --sandbox docker

# Use bubblewrap for isolation
/mcp install postgres --sandbox bubblewrap

# Custom sandbox configuration
/mcp install custom-server --sandbox-config ./sandbox.json
```

### Access Control:
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

## 🏗️ MCP Server Development

### Development Workflow:
1. **Plan**: Define server purpose and tools
2. **Develop**: Implement server with TypeScript/Python
3. **Test**: Test server with OpenCode
4. **Package**: Create distribution package
5. **Publish**: Share with community

### Testing MCP Servers:
```bash
# Test server locally
/mcp test ./custom-server/

# Run server tests
cd mcp-server && npm test

# Integration test with OpenCode
opencode run "Test custom server: echo hello"
```

### Debugging MCP Servers:
```bash
# Enable debug logging
export MCP_DEBUG=1

# View server communication
/mcp debug github

# Trace server execution
/mcp trace custom-server --output trace.json
```

## 🌐 MCP Server Ecosystem

### Community Servers:
- **Official Registry**: https://github.com/modelcontextprotocol/servers
- **Community Contributions**: GitHub topics `mcp-server`
- **Enterprise Servers**: Internal company servers

### Server Standards:
- **Naming**: Use descriptive names (github, postgres, slack)
- **Versioning**: Semantic versioning (1.0.0, 1.1.0, 2.0.0)
- **Documentation**: Include README with examples
- **Testing**: Include comprehensive test suite

### Server Distribution:
```bash
# Publish to npm
npm publish --access public

# Publish to GitHub Packages
npm publish --registry=https://npm.pkg.github.com

# Create standalone binary
pkg dist/index.js --targets node18-linux-x64
```

## 🐛 Troubleshooting MCP Servers

### Common Issues:

**1. Server not starting**
```bash
# Check server command
/mcp status github

# View server logs
/mcp logs github --tail 100

# Test server manually
!npx @modelcontextprotocol/server-github --help
```

**2. Tool not found**
```bash
# List available tools
/mcp tools github

# Check tool permissions
/mcp permissions github list_repos

# Update server version
/mcp update github
```

**3. Authentication errors**
```bash
# Check environment variables
/mcp env github

# Re-authenticate
/mcp auth github --reset

# Use different auth method
/mcp auth github --method oauth
```

**4. Performance issues**
```bash
# Monitor server performance
/mcp stats github --interval 5

# Adjust server resources
/mcp config github --memory 512mb --cpu 1

# Enable caching
/mcp config github --cache enabled
```

### Debug Commands:
```bash
# Dry run server tool
/mcp tool github list_repos --dry-run

# Profile server performance
/mcp profile postgres query "SELECT * FROM users"

# Trace server communication
/mcp trace slack --output trace.json --verbose
```

### Server Recovery:
```bash
# Backup server configuration
/mcp backup --output mcp-backup.tar.gz

# Restore servers from backup
/mcp restore mcp-backup.tar.gz

# Reset server to defaults
/mcp reset github --confirm
```

## 🎯 Best Practices for MCP Servers

### 1. Design for Reliability:
- Handle errors gracefully
- Implement retry logic
- Provide clear error messages
- Include timeout handling

### 2. Prioritize Security:
- Validate all inputs
- Implement rate limiting
- Use secure authentication
- Log security events

### 3. Optimize Performance:
- Implement caching
- Use connection pooling
- Batch operations when possible
- Monitor resource usage

### 4. Ensure Compatibility:
- Follow MCP specification
- Test with multiple OpenCode versions
- Provide migration guides
- Maintain backward compatibility

### 5. Comprehensive Documentation:
- Clear installation instructions
- Detailed tool documentation
- Usage examples
- Troubleshooting guide

### 6. Community Engagement:
- Accept feedback and issues
- Consider feature requests
- Participate in MCP community
- Share learnings and improvements

By leveraging MCP servers, you can extend OpenCode's capabilities far beyond its built-in features, creating a truly customized AI development environment tailored to your specific needs and workflows.

---

## 📚 What's Next?

- [Workflows Guide](WORKFLOWS.md) - Design development workflows
- [FAQ & Troubleshooting](FAQ-TROUBLESHOOTING.md) - Common issues and solutions
- [Back to Main Guide](../README.md)

---

*Last updated: February 2026*