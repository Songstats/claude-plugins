# Songstats for Claude

This plugin bundles the Songstats Music Analytics skill with the production
Songstats remote MCP connector. It uses OAuth and requests only
`mcp:read enterprise:read`; no Enterprise API key is stored in the plugin.

## Install from this repository

From the repository root, add the local marketplace and install the plugin:

```bash
claude plugin marketplace add .
claude plugin install songstats@stats-company
```

For a one-session development check without installing it:

```bash
claude --plugin-dir plugins/songstats
```

Open `/mcp` in Claude Code, select the Songstats server, and complete the OAuth
flow. In Claude or Cowork, open **Customize > Connectors**, select Songstats,
and connect the account when prompted.

The account needs active Songstats or Radiostats product access, or an eligible
Songstats Enterprise API agreement. Successful analytics reads retain the
normal request, search, and object accounting of the agreement that serves the
request.

## Example prompts

- Show my artist's streaming and playlist growth over the last 30 days, and
  compare it with the previous 30 days.
- Which tracks drove the biggest Spotify playlist gains for my label this
  month?
- Compare audience growth and top countries for two artists I can access over
  the last 90 days.

Privacy and terms are available at
<https://songstats.com/privacy-policy> and
<https://songstats.com/terms-of-service>. For setup or account support, contact
<support@songstats.com>.
