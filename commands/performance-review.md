---
description: Read-only cross-channel scorecard for your connected ad platforms with spend, conversions, CPA and ROAS, a blended total, and the change against the previous period.
argument-hint: "[platform] [period, e.g. last week]"
---

# Cross-channel performance review

Load adspirer-analytics-strategy, adspirer-analytics-tools and adspirer-analytics-cross-channel.

Use the platforms and period the user gave. With none given, cover every connected ad platform
for the last 30 complete days, compared with the 30 days before. For a weekly report, use the
last complete Monday to Sunday week in each account's timezone against the week before.

1. Call get_connections_status. Work only on connected platforms. If the user has not said which
   accounts to include and more than one could be meant, list them and ask; never invent an
   account id. Confirm before reporting on a large number of accounts, because each one is a
   separate call.
2. Read each platform through its own router (see references/common-operations.md in
   adspirer-analytics-platform-reports).
3. Report:
   - a channel table: spend, impressions, clicks, CTR, CPC, conversions, CPA, and ROAS where
     available;
   - a blended total computed from comparable totals, with a subtotal per currency when
     currencies differ and no conversion rate is given;
   - the change against the previous period, and the three changes that matter most, each with
     its evidence;
   - gaps: platforms with missing, partial or lagging data, and attribution-window differences
     between channels.
4. End with suggested next questions.

Nothing is changed. For a campaign change, point to a separate Adspirer connector. If a quota or
plan limit blocks the report, stop and explain it. Never buy or upgrade a plan.
