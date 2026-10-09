# Installing DatosIA (for AI agents such as Cline)

DatosIA is a remote MCP server; nothing needs to be installed or built.

1. Add this to the MCP settings file (`cline_mcp_settings.json` or equivalent):

```json
{
  "mcpServers": {
    "datosia": { "url": "https://mcp.datosia.net/mcp", "disabled": false, "autoApprove": [] }
  }
}
```

If the client only supports stdio servers, use the bridge instead:

```json
{
  "mcpServers": {
    "datosia": { "command": "npx", "args": ["-y", "mcp-remote", "https://mcp.datosia.net/mcp"] }
  }
}
```

2. On first use the server asks the user to sign in (OAuth): a browser window opens at datosia.net,
   the user enters their email and the code they receive. No API key is required. Alternatively,
   send a free API key from https://datosia.net/account in an `x-api-key` header.

3. Test it with the `search_data` tool, e.g. `{"question": "población de Quetzaltenango por municipio"}`.
