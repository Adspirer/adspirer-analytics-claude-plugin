# Adspirer Marketing Analytics for Claude

Ask Claude how your marketing is doing and get answers from your real accounts. Adspirer Marketing Analytics is read-only: it reports spend, clicks, conversions, CPA and ROAS by channel and blended across channels, diagnoses funnels and attribution, audits conversion tracking, and reads Google Analytics 4, Search Console and Tag Manager. It cannot create, change, pause or delete anything.

## Use it for

- **Cross-channel reporting:** spend, conversions, CPA and ROAS by channel with a blended total, for any period you name.
- **Attribution and funnels:** find where the funnel breaks, from ad click to site conversion.
- **Web analytics:** Google Analytics 4 traffic and conversions, Search Console queries and pages, and Tag Manager setup.
- **Tracking audits:** grade conversion tracking across ad platforms, GA4, Tag Manager and the Meta Pixel.
- **Wasted spend:** search terms, keywords, placements and audiences spending without converting.
- **Competitors:** the public ads a competitor is running now.

## Install

In Claude Code:

```text
/plugin marketplace add Adspirer/adspirer-analytics-claude-plugin
/plugin install adspirer-analytics@adspirer-analytics
```

On first use, Claude opens Adspirer's OAuth sign-in in the browser. Sign in, then connect the
accounts you want to use at [adspirer.ai/connections](https://adspirer.ai/connections). No API
key or client secret is required. An Adspirer account is required, and plan usage limits apply.

## Get started

Ask:

```text
Show spend, conversions, CPA and ROAS by channel for the last complete 30 days, with a blended total.
Which Search Console queries and pages lost the most clicks this month?
Walk my conversion funnel and tell me where it breaks.
Audit my GA4 and Meta Pixel tracking.
```

Or start with a slash command:

| Command | What it does |
| --- | --- |
| `/adspirer-analytics:setup` | Connect your accounts and get a first look |
| `/adspirer-analytics:status` | Connected accounts and remaining plan usage |
| `/adspirer-analytics:performance-review` | Scorecard against the previous period, with the top problems |
| `/adspirer-analytics:wasted-spend` | Spend that is not converting, with a fix proposed for each item |
| `/adspirer-analytics:tracking-audit` | Grade conversion tracking and list the gaps |

Commands take an optional platform and period, for example `/adspirer-analytics:performance-review last 7 days`. In claude.ai chat, where there is no slash menu, ask for the same thing in words.

## What the agent can do

| Area | Capabilities |
| --- | --- |
| Ad platforms | Google, Meta, TikTok, LinkedIn, Amazon, Microsoft, ChatGPT and Walmart Ads performance |
| Web analytics | Google Analytics 4, Search Console and Tag Manager |
| Diagnostics | Funnel diagnosis, conversion-tracking audit, and wasted-spend analysis |
| Competitor research | Public competitor ads |

This plugin is read-only by design. Requests to create, pause, change budgets, submit URLs for indexing or edit tags are declined. To make changes, use Adspirer Search Ads, Social Ads, Retail Ads or the full Adspirer Advertising Agent.

## What's included

- **Skills:** `adspirer-analytics-attribution`, `adspirer-analytics-competitor-research`, `adspirer-analytics-conversion-tracking`, `adspirer-analytics-cross-channel`, `adspirer-analytics-platform-reports`, `adspirer-analytics-product-help`, `adspirer-analytics-setup`, `adspirer-analytics-strategy`, `adspirer-analytics-tools`, `adspirer-analytics-web-analytics`.
- **A subagent** (`adspirer-analytics-agent`) that coordinates those skills.
- **Slash commands** (`setup`, `status`, `performance-review`, `wasted-spend`, `tracking-audit`) for the most common reports.
- **The Adspirer Marketing Analytics MCP server** connection (`.mcp.json`).

The hosted server is the source of truth for tool names and schemas. The skills teach the agent to
discover the current tools and their parameters instead of hardcoding every operation.

## Safety

- **No writes.** The plugin cannot create, change, pause, resume or delete anything. Requests to
  change an account are declined with a read-only message.
- **No purchases.** The agent never buys, upgrades or renews a plan or paid feature. If a plan limit
  is reached, it stops and explains the limit.
- **Confirmation first** before quota-heavy runs, such as reporting on every account or property.
- **Honest numbers.** Currency, dates, attribution window and data freshness are stated; ratios are
  computed from totals; missing data is never reported as zero; platform-attributed revenue is not
  treated as incremental profit; competitor research covers public ads only.

## MCP and authentication

```json
{
  "mcpServers": {
    "adspirer-analytics": {
      "type": "http",
      "url": "https://mcp.adspirer.com/analytics"
    }
  }
}
```

Authentication uses OAuth 2.1 with PKCE. Claude handles the browser sign-in; the plugin contains no
API keys, tokens, client secrets, or environment variables. Ad-platform credentials stay
server-side with Adspirer and are scoped to the accounts you connect.

## Network and execution surface

The plugin's only MCP server is `https://mcp.adspirer.com/analytics`. It contains no hooks, scripts, telemetry,
local executables, or bundled server code. Skills, the subagent, and commands are Markdown
guidance. Beyond the Adspirer server, the skills may ask Claude to read Adspirer's public
documentation at `adspirer.com/docs` to answer questions about plans and setup.

## Related plugins

Adspirer Marketing Analytics is one of Adspirer's focused plugins. The full
[Adspirer Advertising Agent](https://github.com/Adspirer/adspirer-claude-plugin) covers every
supported platform in one plugin. Installing both is supported; use one connection per task.

## Privacy, support, and source

- Privacy policy: [adspirer.com/privacy](https://www.adspirer.com/privacy)
- Terms: [adspirer.com/terms](https://www.adspirer.com/terms)
- Documentation: [adspirer.com/docs](https://www.adspirer.com/docs/ai-clients/claude-code)
- Support: [support@adspirer.com](mailto:support@adspirer.com)
- Source and issues: [Adspirer/adspirer-analytics-claude-plugin](https://github.com/Adspirer/adspirer-analytics-claude-plugin)

## License

MIT. See [LICENSE](LICENSE).
