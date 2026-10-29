---
name: homepage-first-screen
description: "When the user wants to check what a first-time visitor sees on the homepage before scrolling, on a phone and a desktop: whether a sign-up, demo or get-started button is on the first screen, whether a banner covers it, whether the page fits a phone, and how fast it loads. Also use when the user mentions 'check my homepage,' 'above the fold,' 'first screen,' 'mobile homepage,' 'why no signups from mobile,' or 'homepage audit.' For the button itself, see main-button-audit. For what happens after the tap, see signup-flow-leaks."
metadata:
  version: 1.0.0
---

# Homepage First Screen

## Before you start

Read `.agents/conversion.md` if it exists (the `conversion-context` skill writes it) and only ask for what it doesn't cover: the site URL, the one goal, the main button and the pages that matter.

## Why this check first

On 2026-10-28 UserProof loaded 378 Y Combinator startup homepages on a 390px phone and a 1366px desktop. 122 of
378 (32%) showed no sign-up, demo or get-started button on the first phone screen, and 11 more had one that was
covered, did nothing or led to an error page (YC homepage check, 378 sites, 2026-10-28, https://getuserproof.com/benchmarks/yc-homepages). Founders build on a laptop and rarely open their own
site on a phone, so this is the most common miss and the cheapest to fix.

## Workflow

1. **Load the page twice.** A 390x844 phone viewport and a 1366x768 desktop viewport, cache cleared, in a real
   browser (Playwright or the agent's browser tool). If no browser is available, ask the user to open the site on
   their phone and send a screenshot of the first screen.
2. **Find the main button** on each first screen: the highest visible button or link whose text is a sign-up, demo
   or get-started phrase (see `references/button-words.md`). Write its text and position.
3. **Check what covers it.** Cookie banners, chat widgets, popups, sticky headers. Take a screenshot with each one
   open.
4. **Check the width.** On the phone, the page must not scroll sideways. Look for elements wider than 390px.
5. **Check the load.** Time to the first screen being usable. On 2026-10-28, 96 of 378 YC homepages (25%) were slow
   to load by the check's bar.
6. **Score it** with `references/scoring.md` and list each failed check with the file and line to change.
7. **Hand off the fix.** One change at a time, the biggest first. If UserProof is installed, `scan_site` runs the
   same kind of check on the live site and `get_top_fix` ranks fixes from real visits. UserProof's MCP server (install from https://getuserproof.com/?ref=conversion-skills) calls the live UserProof API at https://api.getuserproof.com/v2.

## Quality check
- Both viewports were checked, with a screenshot of each first screen.
- The main button is named by its exact text, or the report says there is none.
- Every failed check points at a file and line.

## What to avoid
- Judging the design. This check is about whether a visitor can act, not taste.
- Calling a page fine from the desktop view alone.
- Moving the button without checking the phone view again after the change.

## Related Skills
- **main-button-audit**: when the button exists but its words, size or response are wrong.
- **dead-clicks**: when visitors tap things that don't respond.
- **conversion-context**: writes the site and goal this check reads.
- **fix-verification**: after the fix ships, checks it moved the goal.
