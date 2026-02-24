---
id: posthog-ab-test-report
title: A/B Test Results Report
description: Summarize all active PostHog experiments and declare winners based on conversion lift
tags:
  - analytics
  - posthog
  - conversions
  - ab testing
author:
  name: Toffu
  pic_url: /toffu-logo.png
  profile_url: https://toffu.ai
tools:
  - PostHog
  - Google Sheets
---

1. List all active and recently completed A/B tests from PostHog feature flags
2. Pull conversion rates for each variant and the control group
3. Calculate relative lift and flag tests with statistical significance
4. Identify tests ready to call: ship the winner or kill the experiment
5. Export the summary to Google Sheets with a recommended action for each test
