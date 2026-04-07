---
id: b2b-solo-marketer
title: B2B Solo Marketer Starter Kit
description: Full marketing autopilot for a one-person B2B startup marketing team -- daily briefings, LinkedIn posts, ad reports, and competitor monitoring
tags:
  - starter kit
  - b2b
  - linkedin
  - linkedin ads
  - reddit
  - slack
  - competitor analysis
  - content
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - Slack
  - LinkedIn
  - LinkedIn Ads
  - Reddit
  - Google Analytics
  - Google Ads
---

You are setting up a daily marketing operations system for a solo marketer at a B2B startup. This creates a set of scheduled tasks that run automatically and deliver results to Slack.

Before doing anything, explain what's about to happen:

"I'm setting up your marketing autopilot. Here's what I'll do:
1. Check which accounts you have connected (Slack, LinkedIn, Reddit, etc.)
2. Ask a few questions about your company and audience
3. Research your competitors and confirm them with you
4. Create 7 scheduled tasks that will run automatically -- daily briefings, LinkedIn post drafts, ad reports, and competitor monitoring

Everything sends to Slack (or email if Slack isn't connected). LinkedIn posts are always drafts for your approval -- nothing publishes without you.

Let's start."

## Step 1: Check connected accounts

Before anything else, check which integrations I have connected. This starter kit requires:

**Needed for full coverage (ask me to connect if missing):**
- Slack (primary delivery channel -- if not connected, all updates go to my email instead)
- LinkedIn personal profile (for personal post drafts)
- LinkedIn company page (for company posts)
- Reddit (for scanning subreddits -- not required, Reddit browsing works without a connected account)

**Optional (tasks that use these will be skipped if not connected):**
- LinkedIn Ads (weekly ads report)
- GA4 / Google Analytics (website traffic in morning briefing and weekly review)
- Google Ads (ad performance in morning briefing and weekly review)

For any integrations that are missing, tell me which ones are not connected and what I'll miss without them. Ask: "Want to connect these now, or skip those tasks for now? You can always add them later." Wait for my answer before proceeding. If I want to connect, guide me through it. If I want to skip, note which tasks to omit.

If Slack is not connected, all tasks that send to Slack will send to my email instead. Note this when confirming the setup.

## Step 2: Gather context

Read the company's memory and context to learn:
- Company name
- What the company does
- ICP (ideal customer profile): job titles, industries, company size
- Company timezone

Then ask me the following in a single message. Do not create any tasks until you have answers:

1. "Which Slack channel should I send all marketing updates to? (default: #general)" (skip if Slack is not connected -- updates will go to email)
2. "Who is your ideal customer? Give me job titles, industries, and company size. Example: 'VPs of Marketing at B2B SaaS companies, 50-500 employees'" (skip if already known from context)
3. "Describe what your company does in one sentence." (skip if already known from context)
4. "Which subreddits does your audience hang out in? I'll add r/SaaS, r/startups, r/marketing by default." (optional -- say you'll pick based on my industry if left blank)

Skip any question where the answer is already known from company context or memory. If everything is already known, confirm the details with me and ask if anything needs adjusting before proceeding.

Once I answer, determine 10-15 relevant subreddits based on my industry, ICP, and product category. Always include r/SaaS, r/startups, r/marketing. Add vertical-specific ones based on what you learned.

## Step 2b: Research and confirm competitors

Research the company's competitors by searching for companies in the same space. Use what you know about the company's product, ICP, and industry to find 3-5 direct competitors.

Present the list to me: "Based on what you do, these look like your main competitors: [list]. Are these right? Remove or add any."

Wait for confirmation. Use the confirmed competitor list for all tasks below.

## Step 3: Create scheduled tasks

Create all of the following scheduled tasks using create_entity. Use the company timezone for all schedules. Only create tasks for which the required integrations are connected (based on what was determined in Step 1). Write each task prompt using the specific details you gathered -- company name, ICP, subreddits, Slack channel, competitors. Every prompt must be fully self-contained with real values, not references to other tasks or external context.

**Critical: write every Slack/email message for a busy executive who scans on their phone between meetings.** Only surface what changed, what needs attention, or what needs a decision. If nothing is noteworthy, say "all clear" and move on. No preambles, no greetings, no sign-offs, no "here's your report." Just the signal.

---

### Task 1: Morning Marketing Briefing
**Schedule:** Weekdays at 7:30am
**Name:** Daily Marketing Briefing

Prompt should instruct the agent to:
- Send a morning briefing to my Slack channel. Only mention things that need attention. If everything is normal, send "All clear -- nothing unusual overnight."
- Only include a data source if something changed >20% vs the day before or vs same day last week. Format: "LI Ads: spend up 35% ($X), conversions flat" -- one line per exception.
- If anyone mentioned the company or competitors on Reddit in the last 24h, include count + link to the most relevant thread. Otherwise skip.
- Last line: "Focus today:" + the single most important thing to act on. If nothing, skip this line too.
- If a data source is not connected, skip it silently. No filler, no headers, no greetings. Entire message should be 2-4 lines on a normal day.

---

### Task 2: Daily LinkedIn Hot Take
**Requires:** LinkedIn personal profile
**Schedule:** Weekdays at 8:30am
**Name:** Daily LinkedIn Hot Take

Prompt should instruct the agent to:
- Scan the subreddits gathered above for the hottest story from the last 24 hours relevant to the company's ICP -- something people are arguing about, a surprising announcement, a rant that hit a nerve, a tool launch, a trend shift.
- Pick the single best story. Ignore generic advice posts and fluff.
- Draft a LinkedIn post for the founder's personal profile that takes a clear stance on it. Not a summary -- a hot take. What does this mean, why is everyone wrong about it, or what should people actually do about it.
- Post rules: plain language, direct, no buzzwords, no hashtags. Start with a hook that makes someone stop scrolling. Max 150 words. No links or URLs in the post body. Lowercase throughout. Write as a founder sharing a real opinion, not a thought leader performing.
- Send the draft to my Slack channel with one line of context: the source story title + link. Then the draft. Nothing else. Do NOT post it automatically.

---

### Task 3: LinkedIn Company Post
**Requires:** LinkedIn company page
**Schedule:** Monday, Wednesday, Friday at 10:00am
**Name:** LinkedIn Company Post

Prompt should instruct the agent to:
- Create a post for the company's LinkedIn company page.
- Rotate content types: Monday = industry insight or trend take. Wednesday = product-related, framed as a use case or customer problem solved, no feature lists. Friday = curated content, share an interesting article or thread relevant to the ICP with a short take.
- Post rules: professional but not corporate, no hashtags, no emojis, max 200 words. If linking to external content, put the URL in a comment after posting, not in the post body.
- Send draft to my Slack channel. Just the post text, no preamble. Do NOT post it automatically.

---

### Task 4: LinkedIn Ads Weekly Report
**Requires:** LinkedIn Ads
**Schedule:** Monday at 9:00am
**Name:** Weekly LinkedIn Ads Report

Prompt should instruct the agent to:
- Pull the last 7 days of LinkedIn Ads campaign performance data.
- Lead with what needs action: campaigns burning budget with zero conversions, anything with >30% WoW swing in spend or CPA. If nothing is off, say "All campaigns healthy this week."
- Then a compact line per campaign: name, spend, conversions, cost/conv, WoW delta. Skip campaigns with no meaningful change.
- End with 1-3 actions: pause X, increase budget on Y, test Z. Just the action, no justification.
- Send to my Slack channel.

Only create this task if LinkedIn Ads was connected in Step 1.

---

### Task 5: Weekly Content Performance Review
**Schedule:** Friday at 2:00pm
**Name:** Weekly Content & Engagement Review

Prompt should instruct the agent to:
- Send a weekly scorecard to my Slack channel. Lead with the headline: what was the single biggest win and the single biggest miss this week across all channels.
- Then one line per channel with just the key number and its WoW direction: "LI company: 12k impressions (▲40%)" -- skip channels that were flat or not connected.
- End with: "Next week:" + up to 3 content themes to double down on, based on what actually worked. One line each.
- Whole message should fit on one phone screen.

---

### Task 6: Competitor LinkedIn Monitor
**Schedule:** Friday at 3:00pm
**Name:** Weekly Competitor LinkedIn Watch

Prompt should instruct the agent to:
- Check LinkedIn company pages and key executives of the company's top competitors (use the competitors I provided, or the ones you found) for posts from the past 7 days.
- Only report what's worth knowing: a post that got unusual traction, a product launch, a messaging shift, a key hire. If a competitor had a quiet week, skip them entirely.
- End with: "Gaps:" + topics they're covering that we aren't. Max 3 bullets. If no meaningful gaps, say so in one line.
- Send to my Slack channel. If all competitors were quiet, send "Competitors quiet this week. Nothing notable."

---

### Task 7: Competitor Ad Intelligence
**Requires:** LinkedIn Ads
**Schedule:** Wednesday at 10:00am
**Name:** Weekly Competitor Ad Intelligence

Prompt should instruct the agent to:
- Scrape the LinkedIn Ad Library for each confirmed competitor's ads from the last 7 days using scrape_linkedin_ads.
- Analyze what they're running: messaging themes, CTAs, target audience signals, creative formats (single image vs carousel vs video), and any new campaigns that weren't running last week.
- Generate an HTML report using generate_html_report with:
  - One section per competitor: company name, number of active ads, screenshot/preview of their top ads, key messaging themes
  - A "What they're pushing" summary per competitor (2-3 sentences max)
  - A final section: "Opportunities" -- gaps in their messaging that the company could exploit, or angles they're not covering
- Keep the report scannable. No filler analysis. Tables and bullets over paragraphs.
- Send the report link to my Slack channel with a one-line summary: "Competitor ads this week: [one sentence on the most notable finding]"

Only create this task if LinkedIn Ads was connected in Step 1.

---

## Step 4: Confirm

After creating all tasks, send a summary to my Slack channel:

"Marketing autopilot is live. Here's what's running:
[list each task name + schedule]

All updates will land in this channel. Reply to any message to give feedback or approve drafts."

Tell me in chat: list all created tasks with their names and schedules. Note which integrations are required for each and flag any that are not yet connected.
