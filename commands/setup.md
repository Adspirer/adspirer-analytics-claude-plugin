---
description: Connect your ad platforms, Google Analytics 4, Search Console and Tag Manager to Adspirer Marketing Analytics, choose what to report on, and get a first read-only look.
---

# Set up Adspirer Marketing Analytics

Load adspirer-analytics-tools and adspirer-analytics-setup.

1. Call get_connections_status. If it fails because the connector is not signed in, tell the user
   to connect the Adspirer Marketing Analytics connector (in Claude Code: run /mcp, choose
   adspirer-analytics and sign in), then stop and wait. Never ask for a password or token in chat.
2. List what is connected: ad accounts by platform, GA4 properties, Search Console sites and Tag
   Manager containers.
3. If something the user wants is missing, give them https://adspirer.ai/connections and wait. If
   several accounts or properties exist and it is unclear which to report on, ask. Choosing one is
   not a change: this connector has no activate or switch tool, so just pass the chosen id to the
   read tools.
4. Take a first look at the last 30 days on each connected ad platform, using the campaign
   performance operation for that platform (see references/common-operations.md in
   adspirer-analytics-platform-reports). Skip a platform that is not connected; do not invent
   numbers for it.
5. Finish with a short summary: what is connected, what is not, spend and conversions for each
   platform, and what to try next: /adspirer-analytics:performance-review for a cross-channel
   scorecard, /adspirer-analytics:wasted-spend, or /adspirer-analytics:tracking-audit.

This connector is read-only. This command changes nothing and creates no files. Build a brand
workspace only if the user asks for one.
