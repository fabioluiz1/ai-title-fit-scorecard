---
name: ai-title-fit-scorecard
description: Build a personal "AI Engineering Fit Scorecard" — an evidence-based self-assessment that researches real current AI-engineering job titles (AI Engineer, Agentic Engineer, MLOps Engineer, Forward Deployed Engineer, etc.), scores the user's own skills 1-5 from their résumé/workspace/public repos, and ranks how well they fit each title. Use for "am I an AI engineer", "what AI job title fits me", "score my skills against AI job titles", "build me a career fit report for AI roles", or any honest evidence-backed read on where someone stands in the AI job market — trigger even if they only name one title ("am I an agentic engineer?") or ask casually, since the skill still covers the whole landscape. Not for generic résumé review, generic career coaching, or scoring against one company's specific posting.
---

# AI Title Fit Scorecard

Produces a scorecard that answers "which real AI-engineering job titles do I
actually fit, and by how much" — grounded in evidence, not vibes. The output is
a published Artifact: a verdict, a sorted fit-by-title bar chart, a skill
ledger with cited evidence, and a skill × title matrix.

This skill was reverse-engineered from a real multi-hour session building one
of these for a specific person, including several rounds of the person pushing
back on the first draft ("that skill doesn't apply to me," "the weighting is
wrong," "go check this specific repo before you score that"). Expect the same
here: **this is a conversation, not a one-shot report.** Ship a first draft
fast, then keep refining it as the user reacts. Don't try to get it perfect
before showing them anything.

## Why each step matters

**Research must be current and evidence-based, never assumed from title
names.** AI job titles are new and unstable — "Prompt Engineer" was a real
title two years ago and is largely gone now; "AI-Forward Engineer" sounds like
a title but usually isn't one. Guessing what a title means from its name
produces a plausible-sounding but wrong matrix. Verify against real postings.

**Every skill score needs a citable reason, or it's 1, not omitted.** The
temptation is to skip scoring a skill the person clearly doesn't have, or to
give an optimistic "3" out of politeness. Both break the report: an omitted
skill silently vanishes from every title's average instead of dragging it
down, and an ungrounded score can't be defended when the person asks "wait,
why did I get a 3 on that?" A score the user can trace to a specific project or
line in their résumé is worth far more than a fluent-sounding paragraph.

**Weighting must favor what actually defines a title.** A naive average over
every skill a title's job postings mention will let generic, widely-shared
skills (shipping to production, communication, cloud basics) mask a total
absence of the skill that actually makes the title what it is (e.g. model
training for Machine Learning Engineer). Titles with few, sharply-defining
skills need those skills to dominate the score, not get diluted by a long tail
of supporting skills every title shares.

## Step 1 — Research the title landscape

**Check `references/title-landscape.md` first.** It's a dated snapshot of
this exact research from a previous run — titles, definitions,
responsibilities, and the skills × titles matrix, all sourced from real
postings. Read the "Last researched" date at its top.

- **Fresh enough (≲90 days old) and covers what this person needs?** Use it
  as-is, skip straight to Step 2. This is the common case and saves a slow
  research pass for no benefit — the landscape hasn't moved.
- **Stale (>90 days), missing, or the person needs a title it doesn't
  cover** (e.g. they asked about a title that isn't in the file): redo the
  research below, then **overwrite the whole file** with a fresh snapshot
  dated today — regenerate it, don't patch individual lines, since the point
  is one coherent pass per snapshot. This repo is git-tracked, so the old
  snapshot isn't lost — it's just the previous commit. `git log --
  references/title-landscape.md` becomes the timeline of how the title
  landscape has actually shifted over time, and `git diff` between two
  commits shows exactly what changed. If the user seems interested, mention
  that history is there to look at.
- Never silently treat a stale file as current, and never invent a title's
  definition from its name instead of checking the file or re-researching —
  both are the exact "guessing" failure mode this step exists to prevent.

**To do the research** (spawn a research agent, or do it inline with no
subagent tool, using web search):

1. Identify 8-12 real, currently-used AI-engineering job titles — verify each
   one against actual current job postings or credible industry articles, not
   by guessing from the name. If a title the user mentioned turns out not to
   be a real standalone role (this happens — "AI-Forward Engineer" usually
   isn't), say so explicitly rather than inventing a definition for it.
2. For each real title: a one-line definition, its core responsibilities, and
   what it's most often confused with.
3. Build a skills × titles matrix: 15-20 skills spanning the categories that
   actually appear (typically something like *building & integration*,
   *model & data*, *infrastructure & operations*, *people & business* — let
   the research determine the actual groups, don't force these ones). For
   every skill × title cell, mark it **core** (named as a real requirement),
   **supporting** (shows up, not central), or blank (not typically part of the
   role).

Flag titles that are declining (a title that used to be standalone and has
folded into others, e.g. "Prompt Engineer" merging into "AI Engineer") — keep
them in the matrix for now, the user may want them dropped later, but don't
drop them unasked.

## Step 2 — Gather the user's own evidence

Spawn a second agent (in parallel with Step 1, they're independent) to
inventory what the user has actually built or done. Point it at, in rough
priority order:

- Any résumé, LinkedIn text, or job-application notes the user has locally
- Their local project workspace — read READMEs/CLAUDE.md/package.json, don't
  just list folder names
- Their **public GitHub repos** (`gh api users/<handle>/repos`) — these are
  often richer evidence than anything else, because the person forgets what's
  in them. Actually look inside promising repos (`gh api
  repos/<owner>/<repo>/contents/<path>`) rather than trusting the repo
  description alone — a repo titled "terraform-aws" might contain a real
  modular Terraform stack or might be an empty scaffold; only opening it
  tells you which.
- This session's own context, if the user has been doing relevant work in it

Tell it explicitly: report gaps as plainly as strengths ("no evidence of X
found anywhere") rather than filling silence with a generous guess. A missing
skill is real information for this report; softening it defeats the point.

## Step 3 — Score every skill, 1-5

For every skill in the Step 1 matrix, assign 1-5 anchored to something
findable:

- **1** — no evidence anywhere. Score it, don't drop the row — an omitted
  skill disappears from every title's average instead of correctly dragging
  it down.
- **3** — present but not deep (used it, didn't build the core system, or it's
  adjacent to their main stack rather than central to it)
- **5** — repeated, production evidence (shipped it more than once, built the
  system rather than just using one)

Write the evidence next to the score as one citable sentence — a project name,
a résumé line, a specific file path — never a vague "has some experience with
X." If a later evidence source changes the picture for one skill (the user
says "check this specific repo/folder before you score that" — expect this),
re-score just that skill and explain what changed, rather than re-deriving the
whole report.

## Step 4 — Weight and rank

A title's fit score is a weighted average of the user's skill scores, using
the core/supporting marks from Step 1:

```
fit(title) = Σ(score_i × weight_i) / Σ(weight_i)
  where weight_i = 2.0  if skill i is core to title
                  = 0.5  if skill i is merely supporting to title
                  = 0    (skip) if the skill doesn't apply to title at all
```

**Use 2× / 0.5×, not 2× / 1×.** This was tuned deliberately: a naive 2×/1×
split still lets a long tail of supporting skills outweigh a short list of
core ones. A title like Machine Learning Engineer has only 2-3 skills that
truly define it (model training, feature engineering) against 8-9 skills it
merely touches; at 2×/1× those 8-9 supporting skills — most of them skills
nearly every title shares — swamp the 2-3 that actually matter, and someone
with zero ML background can still land a deceptively respectable score. At
2×/0.5× the defining skills dominate the way an actual hiring manager would
weigh them.

Rank titles by exact fit score (not the rounded display value — ties at one
decimal are common and should still order correctly underneath). If the user
questions why a title scored surprisingly high or low, check two things before
re-tuning anything: (1) is a skill mis-scored (go verify), or (2) does that
skill genuinely not apply to that title (check the matrix — a common mistake
is assuming a title needs a skill it doesn't; e.g. MLOps Engineer is about
operating already-built models, not building them, so it typically has no RAG
or vector-database requirement at all).

## Step 5 — Expect iteration, don't over-build the first draft

Publish a first version as soon as Steps 1-4 produce something coherent, then
treat every follow-up as a normal editing pass. Real sessions building this
have included requests like:

- "drop this skill/title, it doesn't apply to me" (recompute every fit score
  that skill fed into — don't just delete the row)
- "check this specific folder/repo before you score that skill" (go look,
  update the score and its evidence, recompute anything downstream)
- "don't mention `<company/project name>` anywhere" (search the whole
  document for it, not just the one place you remember writing it)
- "why does title X score higher than title Y when I don't have skill Z" (this
  usually means the weighting or matrix needs a genuine fix, per Step 4 — take
  it seriously rather than defending the number)

When a skill or title gets dropped, **recompute every fit score it
contributed to** and update every place a stale number or count appears (the
hero verdict, the method card's skill/title counts, chart bars, the matrix
column count and its `colspan`s). A half-updated report with one section still
citing the old numbers is worse than not updating at all — it reads as
careless rather than corrected.

Before naming a current employer in evidence text, consider asking whether
that's fine to publish, or default to "in his/her current role" — this came up
unprompted in the reference session and is an easy thing to get wrong toward
oversharing.

## Step 6 — Build and publish

Load the `artifact-design` skill (utilitarian treatment — this is a personal
report, not a landing page — but still real typographic hierarchy and a
considered palette) and the `dataviz` skill (for the bar chart: single accent
hue since it's one series, sorted, direct-labeled, no dual axis) before
writing HTML, per their own instructions.

`assets/scorecard-template.html` in this skill is a working structural
reference from the session this skill was built from — a warm-paper "ledger"
palette (Fraunces display / Inter body / IBM Plex Mono data face), a hero with
a verdict callout, three method cards, a sorted single-hue bar chart, a skill
ledger table (skill / dot-score / evidence / strength-or-gap flag, skills
ordered strongest → weakest within each category), and a skill × title matrix
(core cells colored green/amber/neutral by whether the score covers, gaps, or
sits mid-way; supporting cells shown faint and uncolored since they rarely
decide fit). Don't reuse its literal palette or copy — it's a reference for
structure and information density, not a brand to inherit. Design fresh
colors, type, and copy for this user's report, following `artifact-design`'s
process.

Order rows within each skill category strongest → weakest score. Order bars in
the fit chart by exact fit score, strongest → weakest.

Publish with the `Artifact` tool. On every later edit in this conversation,
republish the same file path so the URL stays stable — don't create a new
artifact per revision.

## What this skill deliberately doesn't do

It doesn't run a rigorous eval/benchmark loop before shipping (see the
skill-creator skill for that machinery) — this is a personal, conversational
report for one person at a time, and the fast iterate-with-the-user loop in
Step 5 is the actual quality mechanism. If someone wants to harden this into a
polished, publish-once tool for a wider audience, that's a different, heavier
job — point them at skill-creator's eval loop instead of trying to simulate it
here.
