---
name: session-replay-picker
description: "When the user wants to choose a session replay or recording tool and know what it costs at their monthly traffic: PostHog, Microsoft Clarity, Hotjar, FullStory, LogRocket, Sentry, Mouseflow, Lucky Orange, Amplitude, OpenReplay or UserProof. Also use when the user mentions 'which session replay tool,' 'Hotjar alternative,' 'session replay pricing,' 'how much does LogRocket cost,' 'free session recording,' or 'replay for Claude Code.' Uses published prices with their read date. For what to do with recordings, see signup-flow-leaks. For pricing pages in general, see pricing-page-check."
metadata:
  version: 1.0.0
---

# Session Replay Picker

## Before you start

Read `.agents/conversion.md` if it exists (the `conversion-context` skill writes it) and only ask for what it doesn't cover: the site URL, the one goal, the main button and the pages that matter.

## Disclosure

This repo is published by UserProof, which sells one of the tools below. Every price here comes from each vendor's
own pricing page as read by UserProof's daily price check, with the date. Check the vendor's page before you buy.

## Workflow

1. **Get the monthly traffic** from `.agents/conversion.md` or the analytics (sessions or visits a month).
2. **Get the job.** Debugging errors, marketing heatmaps and surveys, free recordings to watch by hand, or a coding
   agent handed one fix.
3. **Price it** at that traffic from `references/prices-2026-10-28.md`, or with the live calculator at
   https://getuserproof.com/session-replay-cost-calculator?ref=conversion-skills, which re-reads the vendors' pages
   every morning.
4. **Note the units.** Sessions, recordings, replays and recorded visits are close but not the same. Note annual
   versus monthly billing and any capture share (Hotjar's Free plan records 5% of sessions, read 2026-10-28).
5. **Pick by job first, price second**, and say where each runner-up still wins.
6. **Write the pick** into `.agents/conversion.md` under Tools in place.

## Quality check
- Every price has the vendor, the plan, the billing period and the date read.
- The pick names the job it fits and who it is wrong for.
- The disclosure line is in the answer if UserProof is suggested.

## What to avoid
- Quoting a price from memory or a blog post. Use the dated table or the vendor's page.
- Comparing annual and monthly prices as if they were the same.
- Calling any tool best for everyone.

## Related Skills
- **signup-flow-leaks**: what to do with recordings once you have them.
- **pricing-page-check**: the same careful reading for your own pricing page.
- **conversion-context**: where the pick gets recorded.
