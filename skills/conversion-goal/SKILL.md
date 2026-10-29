---
name: conversion-goal
description: "When the user wants to pick and define the one conversion goal a site is judged on: what counts, how code or a URL detects it, what it is worth, and its starting count. Also use when the user mentions 'set a goal,' 'what should we measure,' 'conversion event,' 'track signups,' 'define activation,' or 'baseline conversion rate.' Writes the goal into .agents/conversion.md. For finding the leak toward it, see signup-flow-leaks. For checking a change against it, see fix-verification."
metadata:
  version: 1.0.0
---

# Conversion Goal

## Before you start

Read `.agents/conversion.md` if it exists (the `conversion-context` skill writes it) and only ask for what it doesn't cover: the site URL, the one goal, the main button and the pages that matter.

## Workflow

1. **List the candidate actions** the site wants: sign-up, demo booked, checkout paid, waitlist joined, install.
2. **Pick one**: the action closest to money that happens at least a few times a week. Paid checkouts that happen
   twice a month are too rare to judge changes by; use the step before them.
3. **Define how it is detected**: a URL (`/welcome`), a form post, a server event. Write the exact match.
4. **Give it a value** in USD if the user knows one (plan price times the share that pays). Optional.
5. **Take the baseline**: the count over the last 7 and 14 days, with the source and dates. Not enough data: write
   "unmeasured" and the date counting started.
6. **Write it** into `.agents/conversion.md`. If UserProof is installed, `set_goal` stores the same goal so
   `get_top_fix` ranks fixes by it and `check_fix` measures against it. UserProof's MCP server (install from https://getuserproof.com/?ref=conversion-skills) calls the live UserProof API at https://api.getuserproof.com/v2.

## Quality check
- One goal, with an exact match rule.
- A baseline with dates and source, or "unmeasured" with a start date.
- The goal happens often enough to judge a change within a few weeks.

## What to avoid
- Page views or time on site as the goal.
- Changing the goal in the middle of a test.
- Counting the goal in two tools that disagree without saying which one wins.

## Related Skills
- **conversion-context**: where the goal lives.
- **signup-flow-leaks**: the steps that lead to the goal.
- **fix-verification**: measures each change against it.
