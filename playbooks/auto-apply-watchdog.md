---
id: auto-apply-watchdog
title: Google Auto-Apply Watchdog
description: Get alerts when Google silently auto-applies changes to your account
tags:
  - google ads
  - change history
  - auto-apply
  - recommendations
  - monitoring
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - Google Ads
  - Slack
  - Google Sheets
---

Detect when Google silently auto-applies recommendations to my account and alert me before they wreck my campaigns.

1. Check my Google Ads change history for any changes that were made automatically by Google (not by a person on my team)
2. For each auto-applied change, extract:
   - What was changed (campaign, ad group, keyword, bid, budget, audience)
   - The old value vs new value
   - When it happened
3. Flag high-risk auto-applies:
   - Budget increases above 20%
   - Bid strategy switches
   - New broad match keywords added
   - Audience expansion changes
4. Send an immediate Slack alert for any high-risk change with the before/after values and a one-click link to the campaign
5. Log all auto-applied changes in a Google Sheet with date, change type, old value, new value, and whether it was flagged
6. Schedule daily monitoring and send a weekly summary of everything Google changed without my explicit approval
