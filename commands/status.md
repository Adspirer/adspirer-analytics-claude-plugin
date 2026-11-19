---
description: Show which ad accounts, GA4 properties, Search Console sites and Tag Manager containers are connected to Adspirer Marketing Analytics, and how much of your plan's usage is left.
---

# Connection and usage status

Load adspirer-analytics-tools.

1. Call get_connections_status. Show a table: platform or analytics source | account, property,
   site or container name and id | connection health.
2. Call get_usage_status. Show tool calls used, the limit, the plan name and the reset date.
3. Point out anything that needs attention: an expired or failing connection, a platform that is
   not connected, or usage close to the limit.

If the connector is not signed in, tell the user to connect Adspirer Marketing Analytics (in
Claude Code: run /mcp, choose adspirer-analytics and sign in) and stop.

This command only reads. To connect a platform, send the user to
https://adspirer.ai/connections. Never buy, upgrade or renew a plan: if usage has run out, say so,
link https://www.adspirer.com/pricing and wait.
