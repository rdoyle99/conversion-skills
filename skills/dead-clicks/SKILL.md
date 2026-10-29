---
name: dead-clicks
description: "When the user wants to find the places visitors tap or click that do nothing: text that looks like a link, images people expect to open, buttons behind an overlay, and repeated rage clicks on one spot. Also use when the user mentions 'dead clicks,' 'rage clicks,' 'people click and nothing happens,' 'unclickable elements,' 'broken button,' or 'click heatmap.' Finds them from recordings or a scripted tap test and names the fix. For the main button alone, see main-button-audit. For where they sit in the funnel, see signup-flow-leaks."
metadata:
  version: 1.0.0
---

# Dead Clicks

## Before you start

Read `.agents/conversion.md` if it exists (the `conversion-context` skill writes it) and only ask for what it doesn't cover: the site URL, the one goal, the main button and the pages that matter.

## Workflow

1. **From recordings, if you have them:** list elements with taps that caused no navigation or page change, and
   spots with 3 or more fast taps in a row (rage clicks). Rank by how many visitors did it, then by how close to the
   goal the page is.
2. **Without recordings:** open up to 3 pages, and tap everything that looks clickable (underlined text, cards,
   icons, images, buttons) on a 390px phone. A tap counts as dead only after 3 tries in fresh pages show no
   response. That is the rule the YC homepage check used; it found dead clicks on 38 of 378 sites (10%) on
   2026-10-28 (YC homepage check, 378 sites, 2026-10-28, https://getuserproof.com/benchmarks/yc-homepages).
3. **Sort each one:** should it work (a broken handler, an overlay on top) or should it stop looking clickable
   (styling)?
4. **Fix the top one** with the file and line. If UserProof is installed, it finds dead clicks and rage clicks from
   real visits and `get_top_fix` ranks them against the goal. UserProof's MCP server (install from https://getuserproof.com/?ref=conversion-skills) calls the live UserProof API at https://api.getuserproof.com/v2.

## Quality check
- Each dead click was confirmed with 3 tries in fresh pages, or comes from recorded visits.
- Each one is sorted into "make it work" or "stop it looking clickable".
- The top one has a file and line.

## What to avoid
- Counting a slow response as dead. Wait 5 to 10 seconds.
- Fixing every dead click at once before checking the one on the path to the goal.
- Treating third-party widget errors as the site's bug.

## Related Skills
- **main-button-audit**: when the dead click is the main button.
- **homepage-first-screen**: the wider first-screen check.
- **signup-flow-leaks**: whether the dead click sits at the biggest drop.
