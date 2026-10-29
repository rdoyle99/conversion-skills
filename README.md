# Conversion Skills for AI Coding Agents

Skills that teach Claude Code, Codex, Cursor and any agent that reads the [Agent Skills spec](https://agentskills.io)
how to find out why visitors don't sign up, and fix it one change at a time: check the first screen on a phone,
audit the main button, find the leak in the sign-up flow, read the pricing page like a buyer, pick a session replay
tool at your traffic, set one goal, and check each fix afterward.

What makes these different: the numbers are measured and dated. The homepage skills compare your site with a check of
378 Y Combinator startup homepages on a phone and a desktop: 122 of 378 (32%) showed no sign-up, demo or
get-started button on the first phone screen ([YC homepage check](https://getuserproof.com/benchmarks/yc-homepages?ref=conversion-skills),
2026-10-28). The replay skill prices 11 tools from their own pricing pages, read 2026-10-28.

Built by Ryan Doyle, who publishes [UserProof](https://getuserproof.com/?ref=conversion-skills), one of the tools the
replay skill compares. Where UserProof's MCP server helps, a skill says so in one line; every skill works without it.
Found a better way to do something here? [Open a PR](#contributing). A question? [Open an issue](https://github.com/rdoyle99/conversion-skills/issues).

## Install in one paste

Paste this into Claude Code, Codex or Cursor:

```text
Install the conversion skills from https://github.com/rdoyle99/conversion-skills for this project:
1. Run `npx skills add rdoyle99/conversion-skills -a claude-code` (or `-a codex` / `-a cursor` for those agents).
2. Run the conversion-context skill to write .agents/conversion.md for this site, then show me the file.
3. Run homepage-first-screen on the production URL and give me the one fix with the file and line.
```

## How the skills fit together

```
                    conversion-context  (.agents/conversion.md, read first by every skill)
                                  |
          +-----------------------+------------------------+----------------------+
          |                       |                        |                      |
      Goal                    First screen             Flow and pricing        Tools and proof
      conversion-goal         homepage-first-screen    signup-flow-leaks       session-replay-picker
                              main-button-audit        pricing-page-check      fix-verification
                              dead-clicks
```

Every skill ends with a Related Skills section that says which one to run next.

## Skills

<!-- SKILLS:START -->
| Skill | Use it to |
|---|---|
| [conversion-context](skills/conversion-context/) | Set up or update the shared conversion context every other skill in this repo reads first: the site, its one goal, the buyer, the main button, the pages that matter, the tools already installed, and what was tried before. |
| [conversion-goal](skills/conversion-goal/) | Pick and define the one conversion goal a site is judged on: what counts, how code or a URL detects it, what it is worth, and its starting count. |
| [dead-clicks](skills/dead-clicks/) | Find the places visitors tap or click that do nothing: text that looks like a link, images people expect to open, buttons behind an overlay, and repeated rage clicks on one spot. |
| [fix-verification](skills/fix-verification/) | Know whether a change they shipped actually moved the conversion goal: before and after counts on matching days, enough volume to say anything, and a plain verdict of worked, no change, worse or too early. |
| [homepage-first-screen](skills/homepage-first-screen/) | Check what a first-time visitor sees on the homepage before scrolling, on a phone and a desktop: whether a sign-up, demo or get-started button is on the first screen, whether a banner covers it, whether the page fits a phone, and how fast it loads. |
| [main-button-audit](skills/main-button-audit/) | Check the one button that matters on a page: what it says, how big it is on a phone, whether anything covers it, and whether tapping it does something within a few seconds. |
| [pricing-page-check](skills/pricing-page-check/) | Check a pricing page the way a buyer reads it: prices visible without a click, limits in units the buyer understands, monthly versus annual billing stated, a free or trial path, a working button per plan, and an answer to what happens past the limit. |
| [session-replay-picker](skills/session-replay-picker/) | Choose a session replay or recording tool and know what it costs at their monthly traffic: PostHog, Microsoft Clarity, Hotjar, FullStory, LogRocket, Sentry, Mouseflow, Lucky Orange, Amplitude, OpenReplay or UserProof. |
| [signup-flow-leaks](skills/signup-flow-leaks/) | Find where visitors drop out between landing on the site and finishing sign-up, checkout or a booking, and why. |
<!-- SKILLS:END -->

## Installation options

### Option 1: npx skills (recommended)
```bash
npx skills add rdoyle99/conversion-skills            # all skills
npx skills add rdoyle99/conversion-skills --skill homepage-first-screen main-button-audit
npx skills add rdoyle99/conversion-skills --list
```

### Option 2: Claude Code plugin (skills + the UserProof MCP server in one step)
```bash
/plugin marketplace add rdoyle99/conversion-skills
/plugin install conversion-skills
```
The plugin adds UserProof's MCP server (`npx -y github:GetUserProof/userproof`). Its tools need a free UserProof
account (3 sites, 5,000 recorded visits a month, plans read 2026-10-20); the skills run without it.

### Option 3: clone and copy
```bash
git clone https://github.com/rdoyle99/conversion-skills.git
cp -r conversion-skills/skills/* .claude/skills/
```

## The data behind it

| Source | What | Date |
|---|---|---|
| [YC homepage check](https://getuserproof.com/benchmarks/yc-homepages?ref=conversion-skills) | 378 YC startup homepages, Winter 2025 to Fall 2026 batches, 10 checks each on a 390px phone and a 1366px desktop | 2026-10-28 |
| [Session replay cost calculator](https://getuserproof.com/session-replay-cost-calculator?ref=conversion-skills) | published prices of 11 replay tools at 1,000 to 100,000 sessions a month, re-read every morning | 2026-10-28 |
| UserProof MCP (optional) | `get_top_fix`, `check_fix`, `set_goal`, `scan_site`, `check_coverage` against the live UserProof API at https://api.getuserproof.com/v2 | live |

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). `python3 scripts/validate.py` runs the same checks as CI;
`python3 scripts/run_evals.py` runs each skill's evals through a headless agent and writes the results.

## License

MIT
