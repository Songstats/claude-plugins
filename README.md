# Songstats and Socialstats for Claude

Official Claude plugins for Songstats music analytics and Socialstats creator
analytics. Both plugins connect to Stats Company-hosted remote MCP servers over
HTTPS and authenticate through OAuth.

## Plugins

- **Songstats** analyzes authorized artist, label, collaborator, track,
  audience, playlist, curator, and release data.
- **Socialstats** analyzes authorized creator, audience, social-performance,
  public-content, and post data.

The plugins request only the `mcp:read enterprise:read` OAuth scopes. They do
not contain API keys, credentials, customer data, or Songstats backend code.

## Install

Add this repository as a Claude Code marketplace:

```bash
claude plugin marketplace add https://github.com/Songstats/claude-plugins
```

Install either or both plugins:

```bash
claude plugin install songstats@stats-company
claude plugin install socialstats@stats-company
```

Open `/mcp` in Claude Code and complete the OAuth connection for each installed
server. In Claude or Cowork, connect the relevant service from **Customize >
Connectors** when available.

## Support and policies

The product privacy policies explicitly cover OAuth and MCP connections:

- Songstats: <https://songstats.com/privacy-policy>
- Socialstats: <https://socialstats.com/privacy-policy>

For support, contact <support@songstats.com> or <support@socialstats.com>.

## License

MIT
