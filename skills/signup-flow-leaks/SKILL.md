---
name: signup-flow-leaks
description: "When the user wants to find where visitors drop out between landing on the site and finishing sign-up, checkout or a booking, and why. Also use when the user mentions 'signup funnel,' 'where do users drop off,' 'onboarding leak,' 'people start but do not finish,' 'checkout abandonment,' or 'why are signups low.' Maps the steps, counts each, watches recordings at the biggest drop and names one cause. For setting the goal first, see conversion-goal. For checking a fix, see fix-verification."
metadata:
  version: 1.0.0
---

# Sign-Up Flow Leaks

## Before you start

Read `.agents/conversion.md` if it exists (the `conversion-context` skill writes it) and only ask for what it doesn't cover: the site URL, the one goal, the main button and the pages that matter.

## Workflow

1. **Write the steps** from landing to the goal: landing page, main button tap, sign-up page, form submit, email or
   OAuth return, first screen inside. Use the routes in the repo.
2. **Count each step** for the same 7 or 14 days from the analytics the site has. Write the source and dates. If a
   step can't be counted, write "unmeasured" and add an event for it.
3. **Find the biggest drop** by share lost between two steps, not by raw count. If some middle steps are unmeasured,
   still name the most likely drop from what you have, say it is a lead, and name the one event to add first: the
   one that splits the biggest unmeasured gap.
4. **Watch 5 to 10 recordings** of visitors who reached that step and didn't go on. Note what they did last: a tap
   that did nothing, an error, a slow response, a form field that rejected input, a redirect loop.
5. **Name one cause** with the evidence (the sessions, the error, the element) and the file and line.
6. **Ship one fix** and hand it to `fix-verification`. If UserProof is installed, `get_top_fix` does steps 3 to 5
   from recorded visits, and when no finding passes its evidence bar it returns a funnel read (biggest visible leak,
   entry pages, sources). UserProof's MCP server (install from https://getuserproof.com/?ref=conversion-skills) calls the live UserProof API at https://api.getuserproof.com/v2.

## Quality check
- Every count has a source and a date range.
- The cause is backed by recordings or an error, not a guess.
- One fix, tied to the biggest drop.

## What to avoid
- Fixing the step with the most visitors instead of the biggest share lost.
- Calling a leak from fewer than about 20 visitors at that step. Say it is too early.
- Redesigning the whole flow. Change one thing and measure.

## Related Skills
- **conversion-goal**: defines the last step of the flow.
- **dead-clicks**: often the cause at the drop.
- **fix-verification**: checks the fix moved the goal.
