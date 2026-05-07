---
id: meta-ads-daily-dashboard
title: Meta Ads Daily Dashboard with Ad Previews
description: Daily HTML dashboard of your active Meta Ads, with live Instagram embed previews on every ad card, color-coded by performance vs your CPA target
tags:
  - meta ads
  - facebook ads
  - instagram ads
  - dashboard
  - daily reporting
  - previews
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - Meta Ads
  - Email
---

Build a stable-URL HTML dashboard that shows every active ad alongside the actual Instagram preview the audience sees. Refreshes daily and ships by email.

1. Pull ad-level insights from my Meta ad account for the chosen date range (default: month-to-date). Pull `spend`, `impressions`, `clicks`, `ctr`, `cpc`, `cpm`, `actions`, `cost_per_action_type`, plus campaign and ad set names and ids
2. Filter to active campaigns. Exclude catalog and dynamic-product objectives (`PRODUCT_CATALOG_SALES`, `OUTCOME_APP_PROMOTION`) and any campaign whose name contains "catalog", "dynamic", "dpa", or "advantage+ catalog"
3. Pick the primary conversion action for the account (lead / purchase / complete_registration / app_install). Compute CPA per ad, plus account-level totals and averages
4. For each active ad with spend, fetch the Instagram preview using this two-call chain (works for feed posts, Reels, and IGTV):
   - GET `<ad_id>?fields=creative{effective_instagram_media_id,image_url,thumbnail_url}` to get the IG media id Meta serves on Instagram placements, plus a Facebook-side fallback image
   - GET `<ig_media_id>?fields=permalink,thumbnail_url,media_type` to get the canonical permalink
   - The embed URL is `<permalink>/embed/`. Do not parse the permalink, do not assume `/p/`, do not use the creative's `instagram_permalink_url` field directly (it is empty for most direct-uploaded creatives and the URL shape breaks for Reels)
   - Run the fetches in parallel with a small concurrency cap (5–10) so a 200-ad account finishes in under a minute
5. Build the HTML report:
   - Header strip with account name, date range, last-updated timestamp
   - KPI cards: total spend, total results, CPA, ROAS where applicable, impressions, clicks, CTR, CPC, CPM
   - Hierarchy: Campaign → Ad set → Ad cards. Each campaign and ad set shows its rolled-up spend, results, and CPA
   - Each ad card embeds the Instagram preview as an `<iframe>` (320×440), shows the ad name, CPA badge, spend, results, CTR, CPC. For Facebook-only ads with no IG mirror, fall back to the creative's `image_url` or `thumbnail_url`. If neither exists, show a placeholder
   - Sort ads inside each ad set by CPA descending so the worst spenders surface first
6. Color-code each ad card by CPA against my targets: green below the "good" threshold, amber between good and ceiling, red above the ceiling, gray for ads with no results yet
7. Publish via `generate_html_report` and pass the same `existing_report_id` on every run so the dashboard URL stays stable and the most recent version always lives at the same link
8. Email the recipient list a short summary (totals + CPA) with a link to the dashboard
9. Schedule the run daily at my preferred time in my account timezone (default 8 AM)

Parameters to ask me for on first run: ad account id, primary conversion action, CPA "good" and "ceiling" thresholds, recipient emails, currency symbol, account timezone.
