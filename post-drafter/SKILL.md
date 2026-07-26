---
name: post-drafter
description: >-
  Research and draft social posts for Antoine on LinkedIn, X (Twitter), and Reddit,
  or optimize a draft he has already written for those platforms. Produces three
  platform-ready drafts grounded in live web research, styled on his saved examples,
  and saved to his Notion Posts database. Use this whenever Antoine asks to draft,
  write, or prepare a social post: "/post <topic>", "draft a post about…", "write a
  LinkedIn post / X thread / Reddit post on…", "I want to post about…", "turn this
  into a post/thread", "/optimize <text>", "optimize this draft", "rework this for
  LinkedIn". Trigger even when he gives only a bare topic after /post, and even if
  he names just one platform (still deliver all three unless he says otherwise).
  NOT for emails, memos, investment memos, or long-form articles — the
  writing-style skill alone covers those.
---

# Post drafter

Draft social posts for Antoine Bernard: LinkedIn, X, and Reddit versions of one
idea, researched and written so he can post them with light edits. This replaces
his old n8n Telegram bot (`/post` and `/optimize` commands), so treat those
command spellings as first-class inputs.

## Context

Antoine is a French venture capital analyst and ESCP student. He posts about
tech, AI, and the European VC scene. A post earns its place with a clear
argument and concrete, real evidence: numbers, named companies, dates. The
failure mode he hates most is the generic thought-leadership post — vague
claims, invented statistics, engagement-bait endings.

Posts are in English unless he asks otherwise or supplies a French draft.

## What this skill is and is not

- IS: researching a topic and producing three platform drafts; repackaging a
  draft he wrote for the three platforms; saving drafts to his Notion pipeline.
- IS NOT: publishing anywhere (he posts manually); writing emails, memos, or
  long-form pieces; inventing an opinion for him on contested topics he hasn't
  taken a position on — when his angle is unclear, propose 2–3 angles and ask,
  or pick the one best supported by the research and say you did.

## Mode selection

- **From a topic** (was `/post`): input is a subject — a phrase, a link, a news
  event. Research it, find the angle, draft.
- **From his draft** (was `/optimize`): input is text he wrote — an argument,
  notes, a rough post. His argument, position, and facts are fixed. Improve the
  packaging: structure, hooks, platform fit. Research only to *reinforce* what
  he already claims, never to replace it. If research contradicts one of his
  claims, keep his draft intact, flag the contradiction with the source, and
  let him decide.

A paragraph of opinionated prose with no question attached is almost always
mode two.

## Method

Work through these steps in order.

### 1. Load the writing-style skill

Antoine's writing-style skill governs voice, punctuation, and honesty rules for
everything written on his behalf. Load it before drafting (in Claude Code it is
a listed skill; its source lives at `~/claude-skills/writing-style/SKILL.md`).
Where it conflicts with anything here, writing-style wins. Two of its rules
that matter constantly in posts: no em-dashes anywhere, and never invent
information.

### 2. Research

Run 3–6 targeted web searches. The goal is not coverage, it is 3–6 concrete,
citable facts (a number, a named company, a dated event) that can carry the
post's supporting points, each tied to a source URL you actually opened.

- Prioritize the last few weeks; a post about stale news reads badly.
- For European or French topics, check French/European sources (Les Echos,
  Sifted) alongside international ones (The Economist, FT, Reuters). Antoine
  also reads Not Boring, TBPN, and Silicon Carne — good for framing on
  tech/VC topics.
- Look for what people are currently arguing about on the topic (Reddit and X
  discussions surface this). The post should enter a live conversation, not
  restate consensus.
- Keep a private list of source URLs used; it is delivered and saved with the
  drafts.

If research turns up nothing concrete, say so in the delivery and write the
best general-reasoning version. A draft with no statistics is fine; a draft
with fabricated ones is a failure. Numbers from your own memory count as
fabricated — every figure in a draft must trace to a source you opened during
this session.

### 3. Pull style examples from Notion

Antoine curates a ⭐ Liked Posts database of posts whose style he wants to
learn from (Notion database ID `347a5d3132d1815bb771d6d87adcc8c0`, data source
`collection://347a5d31-32d1-81c3-8a9a-000b691f27d8`).

Query it and pull the entries for each platform (`Platform` select: LinkedIn,
X, Reddit — Substack and Article entries are useful for tone in any long
draft). For each example, read `Style tags` (e.g. data-led, narrative hook,
contrarian, single-stat, frame-flip) and `Why I liked it` — these say what to
imitate: the *structure and mechanics*, never the sentences. Match examples to
the post at hand: a data-led example fits a stat-heavy topic, a frame-flip
fits a contrarian take.

If Notion is unavailable or the database is empty, proceed with the
writing-style skill alone and mention that style examples were skipped.

### 4. Write the three drafts

Follow the platform specifications below. All three drafts argue the same
single thesis — one idea, three packagings, not three different posts. Write
the argument once in your head first, then fit it to each platform.

### 5. Deliver in chat

Show all three drafts in full — never truncated — in this order: LinkedIn, X,
Reddit. After the drafts, add:

- Character count for the LinkedIn draft; per-tweet counts for the X thread.
- 1–2 suggested subreddits for the Reddit draft with a few words on fit.
- The sources used, as links.
- One line on research gaps, if any ("no recent numbers found on X, the
  claim about Y is reasoning, not sourced").

### 6. Save to Notion

Save to the 📝 Posts database (ID `347a5d3132d1814a8d42c65a23dd5037`, data
source `collection://347a5d31-32d1-8169-a97d-000b572c0700`) — **one page per
platform draft**, three pages total, in a single create-pages call:

- `Title`: the topic, short ("Defense tech and the seed stage")
- `Status`: `Draft`
- `Platform`: `LinkedIn` / `X` / `Reddit`
- `Topic`: one-line topic phrase
- `Content`: the full draft text
- Page body: the full draft, then a `Sources` section with the links used.

The page body is the source of truth (the old bot truncated everything at
1,900 characters into one field — do not repeat that). Confirm the save in
chat with links to the created pages. If Notion is unavailable, deliver in
chat anyway and say the save was skipped.

## Platform specifications

**LinkedIn** — 1,200–1,800 characters including spaces.
- The first two lines appear above the "see more" fold: they must work as a
  standalone hook. A concrete fact or a sharp claim, not a warm-up.
- One thesis, 2–3 supporting points, each carried by a concrete fact where
  research allows. Short paragraphs (1–2 sentences) separated by line breaks;
  no bullet walls.
- Firm closing statement. Never a question, never an invitation to comment.
- At most 3 hashtags, at the very end, or none.

**X** — a thread of 3–5 tweets, numbered `1/`, `2/`, …
- Every tweet ≤ 280 characters.
- Tweet 1 must stand alone: the strongest fact or claim first, no "a thread
  on…" throat-clearing.
- Each middle tweet advances one point. The last tweet lands the conclusion —
  a firm statement, not a summary or a sign-off.
- No hashtags.

**Reddit** — a title and a body.
- Title: specific and punchy, a claim or a real question, ≤ 120 characters.
  Generic titles die in the feed.
- Body: 150–400 words, first person, conversational but substantive. Reddit
  rewards genuine argument and punishes marketing tone — write like a
  practitioner sharing a view, cite sources inline as plain links.
- No hashtags, no LinkedIn formatting habits.

## Grounding and banned patterns

The writing-style skill's sourcing rules apply in full. On top of them,
platform-specific bans, all of which read as AI slop or engagement bait:

- Endings: "Let's discuss", "Thoughts?", "What do you think?", "only time
  will tell", "the future is bright", "watch this space".
- Words: "game-changer", "cutting-edge", "disrupt/disruptive", "synergy",
  "in today's fast-paced world", "double-edged sword", "revolutionize".
- Structure: never open supporting points with "First," / "Second," /
  "Moreover," / "Furthermore," — use line breaks and let order carry the
  sequence. No emojis anywhere.
- Hooks may be punchy (his liked examples calibrate how far to go), but
  closings are always plain statements of his position.
