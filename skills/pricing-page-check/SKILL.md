---
name: pricing-page-check
description: "When the user wants to check a pricing page the way a buyer reads it: prices visible without a click, limits in units the buyer understands, monthly versus annual billing stated, a free or trial path, a working button per plan, and an answer to what happens past the limit. Also use when the user mentions 'pricing page review,' 'nobody upgrades,' 'pricing confusion,' 'plan comparison table,' 'annual vs monthly,' or 'check my pricing page.' For the button on each plan, see main-button-audit. For comparing tools you might buy, see session-replay-picker."
metadata:
  version: 1.0.0
---

# Pricing Page Check

## Before you start

Read `.agents/conversion.md` if it exists (the `conversion-context` skill writes it) and only ask for what it doesn't cover: the site URL, the one goal, the main button and the pages that matter.

## Workflow

1. **Read the prices from code**, not from copy: the billing config, Stripe price ids or the plan file. Then check the
   page says the same. A mismatch is the first fix.
2. **Prices visible on a phone** without a tap or a slider. If a slider sets the price, say what the default shows.
3. **Billing stated next to the number.** "$29 a month, billed monthly" or "billed annually". Example of why it
   matters: LogRocket's pricing page prints $176 a month on an annual plan at its default of 25,000 sessions
   (read 2026-10-28, https://logrocket.com/pricing). A monthly buyer comparing that number needs the word "annual".
4. **Limits in the buyer's units.** Visits, seats, projects, with what counts as one.
5. **Past the limit.** The page says what happens: cut off, charged, or sampled.
6. **A free or trial path** is on the page, with its limits.
7. **Each plan's button** works on a phone (run `main-button-audit` on the most-bought plan's button).
8. **Write the fixes**, ordered by what each likely costs in lost buyers (a wrong or hidden price first, cosmetic last),
   each with the file and line. Run every check you can on what you were given; mark a check "not checked" only when
   its input is truly missing, and say which input.

## Quality check
- Prices were checked against code or billing, with the file named.
- Every price on the page has its billing period next to it.
- The past-the-limit answer is on the page or flagged as missing.

## What to avoid
- Suggesting a price, even as an example or a break-even sum. This skill checks how prices are shown; what to charge
  is the owner's call.
- Quoting a competitor's price without its page and the date read.
- Hiding the free plan to push the paid one.

## Related Skills
- **main-button-audit**: checks each plan's button.
- **session-replay-picker**: the same reading applied to tools you buy.
- **conversion-context**: holds where the pricing file lives.
