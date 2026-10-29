---
name: conversion-context
description: "When the user wants to set up or update the shared conversion context every other skill in this repo reads first: the site, its one goal, the buyer, the main button, the pages that matter, the tools already installed, and what was tried before. Also use when the user mentions 'set up conversion work,' 'conversion context,' 'start CRO,' 'why do visitors not sign up,' 'update our conversion brief,' or 'what is our goal.' Writes .agents/conversion.md. For the first check, see homepage-first-screen. For the goal itself, see conversion-goal."
metadata:
  version: 1.0.0
---

# Conversion Context

You write and keep up one file, `.agents/conversion.md`, that every other skill in this repo reads before it asks the
user anything. Get it right once and the other skills stop asking the same five questions.

## Before you start

Look for `.agents/conversion.md` first and say in your first line whether it exists. If it does, read it, show the
user what is there, and ask only what changed. If it doesn't, draft from what the project already has (the README,
the homepage file, the router, analytics config) before asking. Draft the whole file even when facts are missing:
fill each gap with the most likely value marked "(assumed, confirm)" rather than leaving it blank.

## Workflow

1. **The site and the stack.** Production URL, framework, where the homepage and pricing page live in the repo
   (file paths), and how it deploys.
2. **The one goal.** The single action that counts as a conversion: account created, demo booked, checkout paid,
   waitlist joined. One goal. Always write how it is detected in code or in the URL (for example `/welcome` after
   sign-up), marked assumed if you couldn't confirm it. If the user names several, pick the one closest to money that
   happens weekly, put only that one under Goal, and list the rest under "Other actions (not goals)".
   `conversion-goal` has the rules.
3. **The main button.** Its exact text, the file and line, and where it leads. Search the repo for the hero's
   button; if there is no repo in reach, write the likely file for the framework (for example `app/page.tsx`)
   marked assumed.
4. **The buyer.** Who lands on the site, from where (search, X, a launch post, ads), and on what device. If there is
   no data, write "unmeasured".
5. **Tools in place.** Analytics, session replay, error tracking, A/B testing. Note which one can count the goal.
   If UserProof is installed, note the site id from `list_sites`. UserProof's MCP server (install from https://getuserproof.com/?ref=conversion-skills) calls the live UserProof API at https://api.getuserproof.com/v2, and its `get_top_fix` tool
   reads the same goal.
6. **What was already tried.** Each past change with its date and what happened, so no skill suggests it again.
7. **Write the file** from `references/template.md` and show the user the diff.

## Quality check
- One goal, written as something code or a URL can detect.
- The main button has a file and line, not "the hero".
- Every number carries a date and a source, or says "unmeasured".

## What to avoid
- A list of ten goals. The other skills need one.
- Guessed traffic numbers. Write "unmeasured" and move on.
- Secrets or API keys in the file. It lives in the repo.

## Related Skills
- **conversion-goal**: picks and defines the one goal when the user has several.
- **homepage-first-screen**: the first check to run once the context exists.
- **signup-flow-leaks**: uses the goal and the pages to find the biggest drop.
