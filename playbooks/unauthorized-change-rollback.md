---
id: unauthorized-change-rollback
title: Unauthorized Change Detector and Rollback
description: Catch unauthorized changes to your ads and roll them back
tags:
  - google ads
  - change history
  - security
  - rollback
  - compliance
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - Google Ads
  - Slack
  - Google Sheets
---

Detect unauthorized or suspicious changes in my Google Ads account and prepare rollback instructions.

1. Ask me for my approved change policy:
   - Approved users (who is allowed to make changes)
   - Approved methods (e.g., only manual UI changes and our API integration, not scripts or Google auto-apply)
   - Protected campaigns that require my approval before any changes
   - Change windows (e.g., only during business hours)
2. Check my Google Ads change history from the last 24 hours and flag violations:
   - Changes by users not on the approved list
   - Changes made through unapproved methods
   - Changes to protected campaigns
   - Changes outside the approved change window
   - Changes auto-applied by Google if I have not opted in
3. For each violation, capture the old and new values so we can roll back
4. Send an immediate Slack alert for each violation with:
   - What was changed, by whom, through which method
   - The old value (what it should be reverted to)
   - The new value (what it was changed to)
5. Log all violations in a Google Sheet with rollback status tracking
6. If I approve, revert the flagged changes to their original values
7. Schedule to run every 4 hours
