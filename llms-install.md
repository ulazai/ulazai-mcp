# Installing UlazAI Media in Cline

This is a hosted remote MCP server. There is nothing to clone, build or install.

Add this entry to `cline_mcp_settings.json`:

```json
{
  "mcpServers": {
    "ulazai": {
      "type": "streamableHttp",
      "url": "https://mcp.ulazai.com/mcp",
      "disabled": false
    }
  }
}
```

Authentication: OAuth with PKCE (S256), dynamic client registration and client ID metadata documents, so MCP clients connect without manual setup. Sign-in runs through Auth0 with your UlazAI account.

With OAuth, Cline opens the sign-in page the first time a tool is used; approve access and return to Cline.

Check the connection by asking: "Which model should I use for a product photo on a white background?"
