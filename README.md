# AI Title Fit Scorecard

A [Claude Code](https://claude.com/claude-code) skill that builds a personal, evidence-based
self-assessment against real current AI-engineering job titles (AI Engineer, Agentic Engineer,
MLOps Engineer, Forward Deployed Engineer, and others) — not a quiz, a scorecard grounded in
your actual résumé, workspace, and public repos.

It researches which AI job titles are real right now (verified against live postings, not
guessed from the name), scores your own skills 1–5 against citable evidence, weights each
title's fit by what actually defines that title rather than generic skills every title shares,
and publishes the result as a report: a verdict, a sorted fit-by-title chart, a skill ledger,
and a skill × title matrix.

## Install

Drop this folder into your skills directory:

```sh
cp -r ai-title-fit-scorecard ~/.claude/skills/
```

Or install the packaged `.skill` file if you have one.

## Use

Ask Claude Code something like:

- "Am I an AI engineer?"
- "What AI job title fits me?"
- "Score my skills against real AI job titles."
- "Am I an agentic engineer?"

See [`SKILL.md`](SKILL.md) for the full method: how titles are researched, how evidence is
gathered and scored, and the weighting formula (core skills 2×, supporting skills 0.5×) tuned
so a title isn't propped up by skills it doesn't actually select for.

[`references/title-landscape.md`](references/title-landscape.md) is a dated snapshot of the
title research (definitions, responsibilities, the skills × titles matrix) so the skill doesn't
re-research from scratch on every run. It carries a "last researched" date and gets regenerated
whenever it goes stale (~90 days) — since this is a git repo, `git log -- references/title-landscape.md`
is a running history of how the title landscape has actually shifted over time.
