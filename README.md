# ZAI Zread MCP Server for Zed

This extension integrates [z.ai Zread](https://zread.ai) as a Model Context Protocol (MCP) server for Zed's Assistant, providing open source repository documentation search, code structure exploration, and file content reading capabilities.

## What is z.ai Zread?

z.ai Zread enables your AI agent to deeply understand open source projects — search documentation, explore repository structure, and read source code files from GitHub repositories.

### ✅ With Zread

- Search documentation, code, and comments in GitHub repositories
- Get directory structure and file lists of repositories
- Read complete code content of specific files in repositories
- Understand repository knowledge, recent issues, PRs, and contributors

## Installation

This extension can be installed from the Zed extension registry.

## Agent Mode Configuration

If you're using Zed's agent mode, you need to enable this context server for your assistant:

1. Open Zed's assistant settings
2. Enable the ZAI Zread MCP server. If you see that the status of the tool is a red dot, make sure you toggle it so that becomes green.
3. Enable the ZAI Zread MCP Server in the active assistant profile. In the chat section, click on the `Write | Ask` button, then click on `tools`, then enable the ZAI Zread MCP Server.

## API Key Configuration

You need a z.ai API key to use this extension.

Add your API key in the extension settings:

```json
{
  "context_server": {
    "mcp-server-zai-zread": {
      "source": "extension",
      "enabled": true,
      "settings": {
        "zai_api_key": "YOUR_ZAI_API_KEY"
      }
    }
  }
}
```

## Usage

Reference GitHub repositories in your prompt:

- `Search the documentation for facebook/react`
- `Show me the directory structure of rust-lang/rust`
- `Read the file src/main.rs from tokio-rs/tokio`
- `What are the recent issues and PRs in vercel/next.js?`

## Available Tools

The ZAI Zread MCP Server provides these tools to the LLM:

- **`search_doc`** — Search for knowledge documentation corresponding to a GitHub repository. Quickly understand repository knowledge, news, recent issues, PRs, and contributors.
- **`get_repo_structure`** — Get the directory structure and file list of a GitHub repository to understand project module splitting and directory organization.
- **`read_file`** — Read the complete code content of specified files in a GitHub repository to deeply analyze implementation details.

## How It Works

The extension uses [supergateway](https://github.com/supercorp-ai/supergateway) to bridge the remote Streamable HTTP MCP server at `https://api.z.ai/api/mcp/zread/mcp` to a local stdio connection that Zed can communicate with.

## Development

Clone the project and build:

```bash
cargo build
```

## License

MIT