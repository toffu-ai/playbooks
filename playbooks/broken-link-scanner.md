---
id: broken-link-scanner
title: Broken Link Scanner
description: Find every broken internal link on your site and get a fix list before Google notices
tags:
  - seo
  - website design
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - Google Search Console
  - Google Sheets
---

1. Fetch your sitemap to get the full list of indexed pages
2. Crawl each page and check all internal links for 4xx/5xx responses
3. Cross-reference with GSC to flag broken links that are receiving impressions
4. Group issues by severity: pages with external inbound links broken are highest priority
5. Export a fix list to Google Sheets with the broken URL, linking page, and suggested redirect
