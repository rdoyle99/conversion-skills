---
name: main-button-audit
description: "When the user wants to check the one button that matters on a page: what it says, how big it is on a phone, whether anything covers it, and whether tapping it does something within a few seconds. Also use when the user mentions 'my CTA,' 'call to action,' 'button not working,' 'nobody clicks sign up,' 'button too small,' or 'what should my button say.' For the whole first screen, see homepage-first-screen. For taps on things that are not buttons, see dead-clicks."
metadata:
  version: 1.0.0
---

# Main Button Audit

## Before you start

Read `.agents/conversion.md` if it exists (the `conversion-context` skill writes it) and only ask for what it doesn't cover: the site URL, the one goal, the main button and the pages that matter.

## Workflow

1. **Name the button.** Its exact text, file and line, and the URL or handler it runs.
2. **Read the words.** Does the text say what happens next ("Start free", "Book a demo")? On 2026-10-28 the most
   common main-button words on 378 YC homepages were "book a demo" (78) and "contact" (25) (YC homepage check, 378 sites, 2026-10-28, https://getuserproof.com/benchmarks/yc-homepages).
   "Contact" tells a visitor less about what happens next than "Book a demo".
3. **Measure the tap target** on a 390px phone. WCAG 2.2 (W3C Recommendation, 2023-10) asks for at least 24 by 24
   CSS pixels (2.5.8), and 44 by 44 for the enhanced level (2.5.5). On the YC check, 95 of 268 main buttons (35%)
   were too small to tap by its bar (2026-10-28).
4. **Check what covers it.** Cookie banner, chat bubble, sticky footer. Tap it with each open.
5. **Tap it and watch** for 5 to 10 seconds: a new page, a new tab, a dialog, a scroll or any change. No response is
   the worst failure on the YC scale (25 points). A slow booking embed that opens late still counts as a response.
6. **Check the destination.** It loads, has no error, and the next step is visible on the phone.
7. **Write one fix** with the file and line. If UserProof is installed, `get_top_fix` returns the highest-impact fix
   from real visits, with the sessions that show it. UserProof's MCP server (install from https://getuserproof.com/?ref=conversion-skills) calls the live UserProof API at https://api.getuserproof.com/v2.

## Quality check
- The button text, size in CSS pixels and tap result are all written down.
- The audit was done on a phone viewport, not only desktop.
- One fix, not a list of ten.

## What to avoid
- Copy changes when the button doesn't respond. Fix the response first.
- Adding a second main button. Two equal buttons split the tap.
- Testing only while logged in. Use a fresh session like a first-time visitor.

## Related Skills
- **homepage-first-screen**: checks whether the button is on the first screen at all.
- **dead-clicks**: finds the taps on things that look clickable but aren't.
- **signup-flow-leaks**: what happens after the button works.
