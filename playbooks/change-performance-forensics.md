---
id: change-performance-forensics
title: Change-to-Performance Forensics
description: Trace a performance drop back to the exact change that caused it
tags:
  - google ads
  - change history
  - performance
  - diagnostics
  - analytics
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - Google Ads
  - Google Analytics
  - Google Sheets
---

When performance drops, automatically investigate what changed and identify the likely cause.

1. Ask me which metric dropped (CPA up, ROAS down, conversions dropped, CTR fell) and the approximate date it started
2. Pull all Change Events from Google Ads for the 3 days before the performance shift
3. For each change, pull the before/after values and identify high-impact modifications:
   - Bid strategy switches (e.g., manual CPC to maximize conversions)
   - Budget cuts or reallocations
   - Keyword additions or pauses
   - Audience targeting changes
   - Ad copy or creative swaps
   - Campaign setting changes (network targeting, device targeting, location targeting)
4. Cross-reference with Google Analytics to check for external factors:
   - Traffic source shifts
   - Landing page issues (bounce rate spikes)
   - Conversion tracking gaps
5. Build a forensic timeline in Google Sheets:
   - Date and time of each change
   - Who made it and through which tool
   - The old and new values
   - Performance metrics for the 3 days before and after the change
   - Likelihood score that this change caused the performance shift
6. Recommend which changes to revert and which to keep
