---
id: gsc-content-opportunities
title: Analyze Google Search Console for New Content Ideas
tags:
  - SEO
  - content
  - analytics
  - blog
author:
  name: Toffu Team
  pic_url: https://toffu.ai/toffu-avatar.png
  profile_url: https://toffu.ai
tools:
  - Google Search Console
  - Google Sheets
  - Browser
---
Analyze Google Search Console data and find opportunities to create content based on the search terms people use. Give me the top 3 ideas that we didn’t already cover on our blog.

1) Inputs
- Ask me for:
  - Blog base URL (e.g., https://example.com) and blog path (e.g., /blog)
  - Google Search Console property to analyze
  - Date range (recommend 90–180 days), Search type = Web, Country (if relevant)

2) Export GSC data
- In Google Search Console → Performance:
  - Set the date range and filters
  - Tab: Queries → Export CSV with columns: Query, Clicks, Impressions, CTR, Position
  - Tab: Pages → Export CSV with columns: Page, Clicks, Impressions, CTR, Position
- Import both CSVs into a single Google Sheet

3) Build an inventory of existing blog content
- Try to fetch `sitemap.xml` and/or `sitemap_index.xml` from the blog base URL and copy all blog URLs and titles into a `Blog Content` sheet
  - If sitemap doesn’t list titles, open the URLs to capture page titles
- If there is no sitemap, fetch the RSS/Atom feed (e.g., /blog/rss.xml or /feed) or ask me for a CSV list of published posts

4) Normalize data in Google Sheets (Queries sheet)
- Add columns:
  - `is_brand`: mark queries that include our brand name(s)
  - `base_topic`: a simplified topic string to group similar queries
  - `opportunity_score`: to prioritize high-impression, low-CTR, mid/poor-position queries
- Example helpers (customize brand terms and stopwords):
  - is_brand (TRUE/FALSE):
    ```
    =REGEXMATCH(LOWER(A2), "(toffu|brandname|productname)")
    ```
  - base_topic (strip common modifiers/stopwords):
    ```
    =TRIM(REGEXREPLACE(LOWER(A2), "(what is|what's|how to|guide|best|top|vs|review|202[0-9]|near me|for|in|on|a|an|the)", ""))
    ```
  - opportunity_score (tune weights as needed):
    ```
    =LN(B2+1) * (1 - MIN(C2, 0.1)/0.1) * (MIN(MAX(D2, 5), 30)/30)
    ```
    Where B2=Impressions, C2=CTR, D2=Position

5) Identify content gaps (Queries vs Blog Content)
- Create a `Topics` range from `Blog Content` titles and slugs (lowercased)
- Mark a query as a gap if ALL are true:
  - `is_brand = FALSE`
  - `Impressions` above threshold (e.g., > 300; adjust for site scale)
  - `Position` between 6 and 30 (not already ranking top 5)
  - No fuzzy/substring match between `base_topic` and any post title/slug in `Blog Content`
- Practical match check (approximate):
  - For each query row, compute:
    ```
    =SUMPRODUCT(--ISNUMBER(SEARCH(base_topic_cell, BlogTitlesRange)))
    ```
    If the result is 0, treat as not covered

6) Cluster similar gaps into candidate topics
- Sort by `opportunity_score` DESC, then by `Impressions` DESC
- Manually group similar `base_topic` values; consolidate overlapping phrasing into one candidate topic
- For each candidate topic, select 3–10 highest-impression queries as supporting keywords

7) Draft the top ideas
- For the top 3 candidate topics (highest combined opportunity):
  - Working title: Use primary phrasing matched to searcher intent ("how to", "what is", comparison, list, use case)
  - Primary keyword: Highest-impression query from the cluster
  - Supporting keywords: 3–8 closely related queries
  - Intent: Informational / Commercial / Comparison / Transactional
  - Angle: Unique value based on your product or POV
  - Outline: 5–8 H2s that directly answer search intent; include FAQs based on queries
  - Internal links: 3–5 relevant existing URLs from `Blog Content`

8) Deliverable
- Return a concise brief with exactly 3 content ideas that are not already covered on our blog:
  - Include: Title, Primary keyword, Intent, Angle, Supporting keywords, Outline (H2s), Internal links
  - Also include a one-line rationale referencing `Impressions`, `CTR`, and `Position`

Notes
- Exclude navigational queries and obvious brand-only terms unless the goal is brand defense
- If you discover that a query maps to a non-blog page (e.g., docs/product), consider a blog explainer that links to the canonical page
- Re-run quarterly; compare to the previous period to spot rising topics