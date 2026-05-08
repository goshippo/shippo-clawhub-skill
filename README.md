# Shippo Skill for ClawHub

Ship packages with Shippo via AI agents. This ClawHub skill gives Claude the knowledge and workflows to validate addresses, compare carrier rates, purchase shipping labels, track packages, and more -- all through natural language.

## Installation

```bash
npx clawhub@latest install shippo
```

## MCP Server Setup

This skill uses the standalone [`@shippo/shippo-mcp`](https://www.npmjs.com/package/@shippo/shippo-mcp) server (npm, stdio transport). **Requires Node.js 18+.**

### 1. Get your API key

Sign up at [apps.goshippo.com/register](https://apps.goshippo.com/register) and grab a test or live API key.

### 2. Configure the MCP server

Add the following to your MCP client configuration (e.g. Cursor `~/.cursor/mcp.json`, Claude Desktop `claude_desktop_config.json`, or Claude Code `~/.claude.json`):

```json
{
  "mcpServers": {
    "shippo": {
      "command": "npx",
      "args": [
        "-y",
        "@shippo/shippo-mcp",
        "start",
        "--api-key-header",
        "ShippoToken YOUR_SHIPPO_API_KEY",
        "--shippo-api-version",
        "2018-02-08"
      ]
    }
  }
}
```

Replace `YOUR_SHIPPO_API_KEY` with your actual key (keep the `ShippoToken ` prefix).

### Manual launch (for debugging)

```bash
npx -y @shippo/shippo-mcp start --api-key-header "ShippoToken YOUR_SHIPPO_API_KEY" --shippo-api-version 2018-02-08
```

This starts the server in stdio mode — it won't show an interactive prompt, it's waiting for MCP protocol messages on stdin.

### Troubleshooting

- **`ReferenceError: Response is not defined`** — Node <18 or stale npx cache. Fix by updating Node (`nvm use 20`) and clearing npx cache (`npm cache clean --force && rm -rf ~/.npm/_npx/`), then restart your MCP client.
- **Auth errors at first tool call** — make sure `--api-key-header` includes the literal `ShippoToken ` prefix before your key (e.g. `"ShippoToken shippo_test_abc123"`, not just `"shippo_test_abc123"`).

## What You Can Do

- Validate and standardize shipping addresses
- Compare rates across USPS, UPS, FedEx, DHL
- Purchase shipping labels (domestic and international)
- Track packages across carriers
- Process bulk shipments from CSV files
- Analyze shipping costs and optimize packaging

## Examples

```
"Compare rates for a 2lb package from San Francisco to New York"
```

```
"Purchase a shipping label for a return from Chicago to LA"
```

```
"Track package 1Z999AA10123456784"
```

## Links

- [Shippo Documentation](https://docs.goshippo.com)
- [Shippo Claude Code Plugin](https://github.com/goshippo/shippo-claude-plugin) -- full plugin experience with extended workflows
- [Sign up for a Shippo API key](https://apps.goshippo.com/register)

## License

MIT
