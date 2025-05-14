[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/iannuttall-flux-ui-mcp-badge.png)](https://mseep.ai/app/iannuttall-flux-ui-mcp)

# Flux UI MCP Server

MCP server for Flux UI component references

This is a TypeScript-based MCP server that provides reference information for Flux UI components. It implements a Model Context Protocol (MCP) server that helps AI assistants access Flux UI component documentation and examples.

## Features

### Tools

- `list_flux_components` - Get a list of all available Flux UI components
- `get_flux_component_details` - Get detailed information about a specific component
- `get_flux_component_examples` - Get usage examples for a specific component
- `search_flux_components` - Search for components by keyword

### Functionality

This server scrapes and caches information from:
- The official Flux UI documentation site (https://fluxui.dev)

It provides structured data including:
- Component descriptions
- Usage examples
- Props
- Code samples

## Development

Install dependencies:
```bash
npm install
```

Build the server:
```bash
npm run build
```

For development with auto-rebuild:
```bash
npm run watch
```

## Installation

### Claude Desktop Configuration

To use with Claude Desktop, add the server config:

On MacOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
On Windows: `%APPDATA%/Claude/claude_desktop_config.json`

#### Option 1: Using local build

```json
{
  "mcpServers": {
    "fluxui-server": {
      "command": "/path/to/fluxui-mcp-server/build/index.js"
    }
  }
}
```

#### Option 2: Using npx command

```json
{
  "mcpServers": {
    "fluxui-server": {
      "command": "npx",
      "args": ["-y", "fluxui-mcp-server"]
    }
  }
}
```

### Windsurf Configuration

Add this to your `./codeium/windsurf/model_config.json`:

```json
{
  "mcpServers": {
    "fluxui-server": {
      "command": "npx",
      "args": ["-y", "fluxui-mcp-server"]
    }
  }
}
```

### Cursor Configuration

Add this to your `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "fluxui-server": {
      "command": "npx",
      "args": ["-y", "fluxui-mcp-server"]
    }
  }
}
```

### Debugging

Since MCP servers communicate over stdio, debugging can be challenging. We recommend using the [MCP Inspector](https://github.com/modelcontextprotocol/inspector), which is available as a package script:

```bash
npm run inspector
```

The Inspector will provide a URL to access debugging tools in your browser. 