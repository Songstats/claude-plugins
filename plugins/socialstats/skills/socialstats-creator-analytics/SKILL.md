---
name: socialstats-creator-analytics
description: Analyze authorized Socialstats creator and public-content data. Use for accessible creator discovery, current or historical social performance, audience geography, source-level trends, content analysis, top-post drivers, and post comparisons through the connected Socialstats MCP server.
---

# Socialstats Creator Analytics

Use Socialstats as the source of truth for account-scoped creator and public-
content analytics. Resolve the creator and access context before requesting
performance data, then select the smallest workflow that answers the question.

## Resolve identity and access

1. Start with `list_accessible_creators` for "my creator," "our profile," or
   any creator name. Use `query`, `limit`, and `offset` when needed.
2. Use `search_socialstats` only when the subject is not resolved from the
   accessible creators and global creator-catalog access is available. Inspect
   `accessible`, `accessible_endpoints`, and `accessible_source_ids`, and
   preserve `access_context` before querying a result.
3. Resolve ambiguous names to a public Socialstats creator ID. Ask the user to
   choose when multiple plausible matches remain.
4. Do not infer access from a public search result. Creator, content, and post
   endpoints can have different access requirements.

## Choose the workflow

- For a current creator overview, call `get_creator_insights`. Start with
  `source=all` unless the user requests a specific platform.
- For public content, call `list_creator_content`, then use a returned post and
  its access context with `get_post_insights`. Public post analytics support
  YouTube, Instagram, and TikTok; do not imply Facebook post coverage.
- For trends or period comparisons, request historic stats with explicit
  `start_date` and `end_date`. Use current stats for current totals.
- For audience questions, use creator audience data from the relevant source.
  Request detailed geography only for a useful two-letter `country_code`.
- For top-content drivers, use top posts or bounded creator content with a
  visible source and metric.
- For an uncommon read-only question, call
  `socialstats_enterprise_api_guide`, then `describe_enterprise_endpoint`, then
  `call_enterprise_endpoint` with only documented parameters.

Keep comparisons to five creators or posts by default. Use the same source,
metric definition, and explicit date window for every subject.

## Interpret results

- Convert relative periods into explicit dates and state the selected window.
- Distinguish current totals, absolute change, and percentage change.
- Compare only like-for-like metrics. Never invent a cross-platform composite
  score or combine incompatible engagement definitions.
- State the Socialstats creators, sources, access scope, and dates used.
- Treat posts, content, audience, and activities as associated evidence; do not
  claim causation from correlation alone.
- Treat missing fields as unavailable, not zero. Treat skipped Facebook public-
  post sections as unsupported, not as evidence of no activity.
- When a bundle returns `partial=true`, use successful sections and identify
  the unavailable endpoints or sources.

## Handle limits and unavailable access

- Respect `retry_after`; do not automatically retry a limited request.
- If authorization is expired or the creator is inaccessible, explain the
  returned recovery action instead of working around Socialstats access
  controls.
- Do not use this plugin to create or revoke provider authorizations, modify
  creator links, retrieve backstage data, or perform Enterprise API writes.
- If the Socialstats MCP connection is unavailable, ask the user to connect or
  reauthorize Socialstats. Do not replace private account analysis with open-
  web estimates or model memory.
