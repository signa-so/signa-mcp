<p align="center"><img src="assets/icon-400.png" width="96" height="96" alt="Signa"></p>

# Signa MCP server

The global trademark API.

Search, screen and monitor trademarks across USPTO, EUIPO, WIPO, UKIPO and more with one API.

[Website](https://signa.so/?utm_source=github&utm_medium=mcp-directory) · [Docs](https://docs.signa.so/mcp/overview) · [Pricing](https://signa.so/pricing) · [Agent skills](https://github.com/signa-so/skills)

## About

Signa is the global trademark API, built for developers and AI agents. This hosted MCP server lets Claude, ChatGPT, Cursor and other MCP clients search and read trademark records from the world's registers, including USPTO, EUIPO, WIPO and UKIPO, in one format.

### What you can do

- Search trademarks by name, class, owner, status and office, with fuzzy, phonetic and lookalike-character matching. Each result shows why it matched.
- Read the full record: status, goods and services, classes, owners, attorneys, events and proceedings.
- Research owners and their portfolios, with registry owners linked to the companies behind them.
- Look up attorneys and law firms and the marks they represent.
- Find the Nice classes for a product or service, and check goods and services wording.
- Check office rules such as deadlines, prosecution steps and opposition periods.
- Monitor marks with watches and alerts (API key).

### Who it's for

Trademark attorneys and paralegals, brand and legal teams, founders checking a name, and developers building trademark tools.

### The data

Records come straight from the official registries and are kept current. Every record carries its source date, and Signa publishes which offices it covers. Ask Signa which offices are live, or see the [docs](https://docs.signa.so/mcp/overview).

## Connect

Server URL: `https://api.signa.so/mcp` (Streamable HTTP, hosted, nothing to install)

Sign in with your Signa account (OAuth). For scripts and headless clients, use an API key instead. Free to start, no card required, with simple, public [pricing](https://signa.so/pricing).

**Claude Code**

```bash
claude mcp add --transport http signa https://api.signa.so/mcp
```

**Claude.ai and Claude Desktop**: Settings → Connectors → Add custom connector, paste `https://api.signa.so/mcp`, sign in. Or add Signa from the [Claude directory](https://claude.ai/directory/signa).

**ChatGPT** (plans with MCP connectors): add a connector with `https://api.signa.so/mcp` and choose OAuth.

**Cursor** (`.cursor/mcp.json`)

```json
{ "mcpServers": { "signa": { "url": "https://api.signa.so/mcp" } } }
```

**VS Code** (`.vscode/mcp.json`)

```json
{ "servers": { "signa": { "type": "http", "url": "https://api.signa.so/mcp" } } }
```

**API key instead of OAuth** (any client that accepts headers)

```json
{ "headers": { "Authorization": "Bearer sig_YOUR_KEY" } }
```

**Clients that only run local (stdio) servers**

```bash
npx mcp-remote https://api.signa.so/mcp
```

## Example prompts

- Is BRIGHTLY already registered for software in the US, EU or UK? Check classes 9 and 42.
- Which Nice classes should a company selling smart home cameras and a subscription app file in?
- Find marks similar to AURORA in class 9 at EUIPO, including ones that sound alike.
- Show the full record for US trademark 1939139: status, owner, classes and recent events.
- List Nike's trademarks at UKIPO with their current status.
- List TTAB oppositions filed against marks owned by Apple Inc. in the last 12 months.
- How long is the opposition period at EUIPO, and when does it end for this application?

## Tools

Tools are grouped below; the full list with scopes is in [Tools & permissions](https://docs.signa.so/mcp/overview).

| Group | What it does | Access |
|---|---|---|
| Search | Find marks by name, class, owner, status and office | OAuth or API key |
| Trademarks | Full records, events and proceedings for a mark; batch lookups | OAuth or API key |
| Owners and entities | Registry owners, the companies behind them, and their portfolios | OAuth or API key |
| Attorneys and firms | Attorneys and firms of record, their clients and marks | OAuth or API key |
| Proceedings | Oppositions, cancellations and other proceedings | OAuth or API key |
| Reference | Offices, jurisdictions, status codes, Nice classes, goods and services, design codes, deadline and opposition rules | OAuth or API key |
| Monitoring | Create, pause and manage watches; alerts, webhooks and events | API key |
| Account | Plan, pricing and usage | Usage needs an API key |

With OAuth, the server exposes read-only tools. Write tools only manage your own watches and need an API key. Signa never files applications or changes official records.

## FAQ

**Is it free?** Free to start, no card required. Paid plans add volume; see [pricing](https://signa.so/pricing).

**Which offices does it cover?** Major registers including USPTO, EUIPO, WIPO and UKIPO, with more added regularly. Ask Signa "which offices do you cover?" for the live list.

**Can it change anything?** Signed in with OAuth, it is read-only. With an API key it can also create and manage your own watches. It never files applications or touches official records.

**Where does the data come from?** From the official trademark registries. Every record shows its source date.

**Is this legal advice?** No. Signa is a research tool. Results don't establish legal clearance or replace advice from a qualified attorney.

## This repository

The server is hosted by Signa; its code is not in this repository. This repository holds the public listing for MCP directories and registries: this README, [`server.json`](server.json) for the official MCP Registry, a Cursor plugin ([`.cursor-plugin/plugin.json`](.cursor-plugin/plugin.json) and [`mcp.json`](mcp.json)) and the logo.

Support: support@signa.so · [signa.so/contact](https://signa.so/contact)

Signa Technologies Ltd
