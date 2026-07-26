---
name: save-liked-post
description: >-
  Capture a social post Antoine likes into his ⭐ Liked Posts Notion database,
  fully structured: author, platform, full content, style tags from his fixed
  vocabulary, why he liked it, and the save date. Use whenever Antoine pastes a
  post (or gives a link to one) and asks to keep it: "save this post", "add this
  to my liked posts", "save to liked posts", "keep this one", "garde ce post",
  "ajoute ça aux liked posts", or when he pastes post text with a short reaction
  like "love the hook on this". Works for LinkedIn, X, Reddit, Substack, and
  article excerpts. NOT for drafting or optimizing his own posts (that is
  post-drafter) and not for logging posts he published himself.
---

# Save liked post

Turn a pasted post into a structured entry in Antoine's ⭐ Liked Posts database
(Notion database ID `347a5d3132d1815bb771d6d87adcc8c0`, data source
`collection://347a5d31-32d1-81c3-8a9a-000b691f27d8`). This database feeds the
post-drafter skill: its entries are the style examples future drafts imitate,
so a well-filled entry directly improves his future posts.

## What he gives you

Usually the pasted text of a post, sometimes with the author's name attached,
sometimes with a URL, sometimes with a one-line reaction ("the hook is great").
Accept any of it. If he gives only a URL: fetch it if the page is publicly
readable (Substack, Reddit, blogs). LinkedIn and X pages usually cannot be
fetched; in that case ask him to paste the text rather than guessing — never
reconstruct a post's content from memory or from the URL alone.

## Fields to fill

- **Author** (title): the person or publication who wrote the post. If it is
  nowhere in what he pasted, ask.
- **Content** (text): the full post text, verbatim, untranslated, uncorrected.
- **Platform** (select): one of `LinkedIn`, `X`, `Substack`, `Reddit`,
  `Article`. Infer from the URL or the format (thread numbering says X,
  "see more" prose blocks say LinkedIn, title+body says Reddit). State the
  inference in your confirmation; only ask when genuinely ambiguous.
- **Style tags** (multi_select): choose 1–3 from the fixed vocabulary only:
  `data-led`, `narrative hook`, `contrarian`, `thread-opener`, `list-format`,
  `single-stat`, `frame-flip`, `question-hook`. Never invent new tags. Pick
  what the post actually does, not what it is about.
- **Why I liked it** (text): the most valuable field — post-drafter reads it
  to know what to imitate. If Antoine gave a reaction, use his words. If he
  gave nothing, ask him once, briefly ("why this one?"). If he answers "just
  save it", write your own one-line reading of what makes the post work,
  prefixed "(inferred)".
- **Saved at** (date): today.
- Leave **Embedding** and **Category** empty; they belong to other automations.

## Method

1. Parse what he pasted; separate post content from his commentary.
2. Check for a duplicate: query the data source for an entry whose Content
   starts the same way. If one exists, say so and stop unless he insists.
3. Create the page with all fields. Multiple posts in one message become
   multiple pages in one create-pages call.
4. Confirm in one line with the Notion link and the tags you chose, e.g.
   "Saved. Author Packy McCormick, Platform Substack, tags data-led +
   frame-flip." No summary of the post back at him.

If Notion is unreachable, say so and output the structured entry as text he
can paste later; do not silently drop the capture.
