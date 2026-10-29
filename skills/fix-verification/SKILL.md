---
name: fix-verification
description: "When the user wants to know whether a change they shipped actually moved the conversion goal: before and after counts on matching days, enough volume to say anything, and a plain verdict of worked, no change, worse or too early. Also use when the user mentions 'did the fix work,' 'measure the change,' 'before and after,' 'A/B result,' 'conversion went up?,' or 'verify the fix.' For the goal it measures against, see conversion-goal. For the next fix to try, see signup-flow-leaks."
metadata:
  version: 1.0.0
---

# Fix Verification

## Before you start

Read `.agents/conversion.md` if it exists (the `conversion-context` skill writes it) and only ask for what it doesn't cover: the site URL, the one goal, the main button and the pages that matter.

## Workflow

1. **Write down the change**: what shipped, the commit, and the date and hour it went live. Check it is live on the
   production URL before counting.
2. **Pick the windows**: the same number of whole days before and after, matching days of the week. 7 and 7 is a
   good default; 14 and 14 for low traffic.
3. **Check nothing else shipped** in either window yourself: run `git log --since <before start> --until <after end>`
   on the deploy branch and read the Already tried table. Another change in the window means the verdict covers both.
4. **Count the goal and the visitors** in each window from the same source. Write source and dates.
5. **Compare the rate**, not the raw count, so a traffic spike doesn't look like a win.
6. **Call it** with `references/verdicts.md`: worked, no change, worse, or too early. Say the verdict in the first
   line, with both rates.
7. **Write the row now** into the Already tried table of `.agents/conversion.md` (date, change, commit, before, after,
   verdict), filled in with the real numbers, and show the edited table. Don't leave placeholders for the user. If UserProof is
   installed, `mark_fix_applied` records the ship time and `check_fix` compares the goal before and after for you.
   UserProof's MCP server (install from https://getuserproof.com/?ref=conversion-skills) calls the live UserProof API at https://api.getuserproof.com/v2.

## Quality check
- The change was confirmed live before the after-window started.
- Both windows use the same source, length and days of the week.
- The verdict says "too early" when the counts are small.

## What to avoid
- Declaring a win from one good day.
- Shipping a second change inside the after-window. It mixes the two.
- Comparing against a window that had a launch, an outage or a holiday.

## Related Skills
- **conversion-goal**: the goal this skill measures.
- **signup-flow-leaks**: finds the next fix once this one is judged.
- **main-button-audit**: the usual first fix to verify.
