---
id: campaign-drift-detector
title: Campaign Drift Detector
description: Spot campaigns that have drifted from their intended settings over time
tags:
  - google ads
  - change history
  - campaign management
  - audit
  - compliance
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - Google Ads
  - Google Sheets
  - Gmail
---

Detect when campaigns have drifted from their intended setup due to accumulated changes over time.

1. Ask me for my campaign standards (target CPA, budget caps, approved bid strategies, required negative keyword lists, approved locations, network settings)
2. Pull the current state of all active campaigns from Google Ads
3. Compare current settings against my stated standards and flag deviations:
   - Campaigns running bid strategies that differ from the approved strategy
   - Budgets that exceed the approved cap
   - Missing negative keyword lists that should be applied
   - Location targeting that includes regions I do not serve
   - Network settings that were changed (e.g., Search Partners enabled when it should not be)
4. Use the Change Event log to trace when and who caused each drift:
   - When was the setting changed from the standard?
   - Was it a human, a script, or Google auto-apply?
5. Build a drift report in Google Sheets:
   - Campaign name, drifted setting, expected value, current value
   - Who changed it and when
   - Recommended fix
6. Email me the drift report
7. Schedule a monthly audit
