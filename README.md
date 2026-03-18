# Shippo Skill for ClawHub

Ship packages with Shippo via AI agents. This ClawHub skill gives Claude the knowledge and workflows to validate addresses, compare carrier rates, purchase shipping labels, track packages, and more -- all through natural language.

## Installation

```bash
npx clawhub@latest install shippo
```

## MCP Server Setup

This skill requires a connection to the Shippo MCP server. Follow both steps below.

### 1. Set your API key

```bash
export SHIPPO_API_KEY="ShippoToken shippo_test_xxxxx"
```

Replace `shippo_test_xxxxx` with your actual Shippo API key. You can get one at [apps.goshippo.com/register](https://apps.goshippo.com/register).

### 2. Configure the MCP server

Add the following to your MCP configuration:

- **URL:** `https://app.getgram.ai/mcp/shippo-mcp-beta`
- **Header:** `Mcp-Shippo-Merged-Api-Key-Header` with the value of your API key (e.g., `ShippoToken shippo_test_xxxxx`)

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
