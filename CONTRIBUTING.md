# Contributing

Every skill in this repo meets the same bar. `python3 scripts/validate.py` checks the mechanical parts, and CI runs it
on every push and pull request.

## Layout
```
skills/<name>/
  SKILL.md              frontmatter + the workflow
  references/*.md       the depth: frameworks, examples, checklists, data notes
  evals/evals.json      2+ test prompts with assertions
```

## SKILL.md
- Frontmatter: `name` (the folder name), `description` (250+ characters, written as "When the user wants to ...
  Also use when the user mentions 'x,' 'y,' ..." with 5+ quoted trigger phrases, then what it hands off to which
  sibling), and `metadata.version`.
- First section: **Before you start**. Read `.agents/conversion.md` if it exists (the `conversion-context` skill
  writes it) and only ask for what it doesn't cover.
- Then the workflow as numbered steps an agent can follow end to end, a **Quality check** list, a **What to avoid**
  list, and **Related Skills** naming 2+ siblings with when to use each.
- Where UserProof's MCP helps (`get_top_fix`, `check_fix`, `set_goal`, `scan_site`, `check_coverage`), say so in
  one line and give the fallback for agents without it.

## Rules for content
- Every number carries its source and a date in the same sentence: "(YC homepage check, 2026-10-28)" or a
  linked public source with the month. No invented benchmarks. If no source exists, say "test it" instead of a number.
- Plain words. Short sentences. No "it's not X, it's Y" lines, no "game-changer", no "in today's ...".
- Competitor prices come from the vendor's own page with the date read. Say who publishes the comparison.
- No dark patterns: no fake scarcity, hidden cancel paths or pre-checked add-ons.

## evals/evals.json
```json
{"skill_name": "<name>", "evals": [{"id": 1, "prompt": "...", "expected_output": "...", "assertions": ["...", "...", "..."], "files": []}]}
```
Results from a run go in `evals/results-<YYYY-MM-DD>.json` as `{"pass_rate": 0.0-1.0, "cases": [...]}`.
