# Socialstats for Claude

This plugin bundles the Socialstats Creator Analytics skill with the production
Socialstats remote MCP connector. It uses OAuth and requests only
`mcp:read enterprise:read`; no Enterprise API key is stored in the plugin.

## Install from this repository

From the repository root, add the local marketplace and install the plugin:

```bash
claude plugin marketplace add .
claude plugin install socialstats@stats-company
```

For a one-session development check without installing it:

```bash
claude --plugin-dir plugins/socialstats
```

Open `/mcp` in Claude Code, select the Socialstats server, and complete the OAuth
flow. In Claude or Cowork, open **Customize > Connectors**, select Socialstats,
and connect the account when prompted.

The account needs active Socialstats creator, team, bundle, or Professional
access, or an eligible Socialstats Enterprise API agreement. Successful
analytics reads retain the normal request, search, and object accounting of the
agreement that serves the request.

## Example prompts

- Show my creator's Instagram follower growth over the last 30 days, and
  compare it with the previous 30 days.
- Which YouTube, Instagram, or TikTok posts drove the most engagement for my
  creator this month?
- Compare audience growth and top countries for two creators I can access over
  the last 90 days.

Privacy and terms are available at
<https://socialstats.com/privacy-policy> and
<https://socialstats.com/terms-of-service>. For setup or account support,
contact <support@socialstats.com>.
