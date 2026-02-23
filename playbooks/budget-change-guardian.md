---
id: budget-change-guardian
title: Budget Change Guardian
description: Get alerts whenever someone changes your ad budgets unexpectedly
tags:
  - google ads
  - change history
  - budget
  - alerts
  - spend protection
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - Google Ads
  - Slack
---

Monitor all budget changes across my Google Ads account and alert me when anything unexpected happens.

1. Check my Google Ads change history for any budget changes in the last 24 hours
2. For each budget change, extract:
   - Which campaign was affected
   - Old budget vs new budget (exact dollar amounts)
   - Who made the change
   - How it was made (manually, via API, via automated rule, or auto-applied by Google)
3. Alert me in Slack if any of these conditions are met:
   - Budget increased by more than 20% in a single change
   - Budget was changed by someone outside my approved list of users
   - Budget was changed automatically by Google without my approval
   - Multiple budget changes happened on the same campaign within 24 hours
   - Total daily budget across all campaigns exceeds my monthly target divided by days remaining
4. Include in the alert: campaign name, old budget, new budget, who changed it, and how it was made
5. Schedule to run every 6 hours
