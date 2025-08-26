---
id: detect-conversion-drops
title: Detect Conversion Drops
tags:
  - ga4
  - monitoring
  - conversions
  - alerts
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - Google Analytics 4
  - Slack
---

1. Pull daily conversions from GA4 for key events (signups, demo bookings, purchases)  
2. Compare last 7 days vs previous 7 days  
3. If drop >20%, trigger alert in Slack with affected channel/page breakdown  
4. Investigate:  
   - Traffic source shifts (organic vs paid)  
   - Technical issues (broken forms, tracking outages)  
   - Seasonal patterns  
5. Recommend corrective actions (fix tracking, update Ads, re-optimize top landing pages)
