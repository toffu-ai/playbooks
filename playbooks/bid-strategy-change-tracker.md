---
id: bid-strategy-change-tracker
title: Bid Strategy Change Tracker
description: Track every bid strategy change and measure if it helped or hurt
tags:
  - google ads
  - change history
  - bidding
  - smart bidding
  - optimization
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - Google Ads
  - Google Sheets
  - Slack
---

Track every bid strategy change across my account and measure whether it helped or hurt performance.

1. Query Change Events for all campaign-level changes where the bidding strategy fields were modified
2. For each bid strategy change, extract:
   - Campaign name
   - Old bid strategy vs new bid strategy (e.g., Manual CPC to Target CPA, Target CPA to Maximize Conversions)
   - Target values (old target CPA vs new target CPA)
   - Who made the change and through which tool
   - Date and time
3. For each change that is at least 7 days old, pull performance metrics for 7 days before and 7 days after:
   - CPA, ROAS, conversion volume, impression share, average CPC
4. Classify each change as: improved performance, hurt performance, or no significant impact
5. Log everything in a Google Sheet with the before/after bid strategy, before/after performance, and the verdict
6. Send a Slack alert whenever a new bid strategy change is detected, with a reminder to check back in 7 days for the impact analysis
7. Schedule weekly execution
