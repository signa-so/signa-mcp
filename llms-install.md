# Installing the Signa MCP server

Signa is a hosted, remote MCP server. There is nothing to clone, build or run locally.

- Server URL: `https://api.signa.so/mcp`
- Transport: Streamable HTTP
- Auth: OAuth (the user signs in with a Signa account in the browser), or an API key sent as `Authorization: Bearer sig_…`

## Cline

Add this entry to `cline_mcp_settings.json`:

```json
{
  "mcpServers": {
    "signa": {
      "type": "streamableHttp",
      "url": "https://api.signa.so/mcp",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

With the Cline CLI, the same thing in one command:

```bash
cline mcp add signa https://api.signa.so/mcp --transport streamableHttp
```

The first connection returns 401 until the user signs in. Cline then registers itself with Signa's OAuth server and opens a sign-in page at `app.signa.so`. Ask the user to sign in (or create a free Signa account, no card required) and approve access. After that, the tools are available.

## API key instead of OAuth

For headless use, skip the browser sign-in and send an API key. Users create keys at https://app.signa.so.

```json
{
  "mcpServers": {
    "signa": {
      "type": "streamableHttp",
      "url": "https://api.signa.so/mcp",
      "headers": { "Authorization": "Bearer sig_YOUR_KEY" }
    }
  }
}
```

OAuth sign-in exposes read-only tools. Watches, alerts and usage tools need an API key.

## Check it works

Ask: "Use Signa to list the trademark offices it covers." The `list_offices` tool should answer.
