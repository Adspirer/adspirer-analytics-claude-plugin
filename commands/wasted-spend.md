---
description: Read-only review of ad spend that is not converting, such as search terms, keywords, placements and audiences, across your connected ad platforms, with a fix proposed for each.
argument-hint: "[platform] [period, e.g. last 30 days]"
---

# Wasted-spend review

Load adspirer-analytics-tools and adspirer-analytics-platform-reports.

Use the platforms and period the user gave. With none given, cover every connected ad platform
for the last 30 complete days.

1. Call get_connections_status. Work only on connected platforms, and confirm the accounts when
   more than one could be meant.
2. Run each platform's wasted-spend and search-term reads through its own router (see
   references/common-operations.md in adspirer-analytics-platform-reports).
3. Separate rows with spend and no conversions from rows with a high cost per conversion. Do not
   call a row wasted when the sample is small, when conversions are still arriving, or when
   conversion tracking looks broken.
4. Report the top items by spend with the evidence, the total at stake per currency, and a
   proposed fix for each one (a negative keyword, an exclusion, or a bid or budget change) for the
   user to apply in their own tools or through a separate Adspirer connector.

This connector is read-only. Nothing is changed by this command.
