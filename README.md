# Claude skills

A personal collection of [Claude skills](https://docs.anthropic.com/en/docs/claude-code/skills).
One folder per skill; each folder has a `SKILL.md` (plus any supporting files).

## Skills

| Skill | What it does | Status |
|-------|--------------|--------|
| [writing-style](writing-style/SKILL.md) | Antoine's personal writing style and standards for any text written on his behalf (FR/EN) | Uploaded to claude.ai |
| [contract-triage](contract-triage/SKILL.md) | Fast first-pass triage of an incoming contract for Alice & Bob's Legal team — GREEN/YELLOW/RED verdict | Uploaded to claude.ai |
| [contract-deep-review](contract-deep-review/SKILL.md) | Clause-by-clause legal review with per-contract-type checklists, severity ratings, and redlines | Uploaded to claude.ai |
| [update-rebuild-recipe](update-rebuild-recipe/SKILL.md) | Refresh the Mac rebuild recipe (app + Homebrew inventory) in the private memory-backup repo | Claude Code only (local) |
| [restore-mac](restore-mac/SKILL.md) | Set up a fresh Mac from the rebuild recipe — apps, CLI tools, dotfiles, fonts, skills, memory | Claude Code only (local) |
| [post-drafter](post-drafter/SKILL.md) | Research + draft LinkedIn/X/Reddit posts in Antoine's voice, or optimize a draft he wrote; saves to the Notion Posts DB (replaces the n8n Telegram bot) | Uploaded to claude.ai |
| [save-liked-post](save-liked-post/SKILL.md) | Paste a post you like, get a fully structured entry in the ⭐ Liked Posts Notion DB (author, platform, style tags, why) — feeds post-drafter | Not yet uploaded |

[`positions.md`](positions.md) is the Alice & Bob negotiation playbook the contract
skills were designed around — update it, not the skills, when positions change.

## How this is organized

Each skill is a self-contained folder:

```
<skill-name>/
  SKILL.md              # the skill (YAML header + instructions)
  <supporting files>    # optional: checklists, references, templates
```

`_template/` holds a starting point for new skills.

## Using a skill

- **Paste method (any Claude account):** open the skill's `SKILL.md`, paste it into
  a chat as instructions, then give Claude the input to work on. If the skill loads
  supporting files, paste the relevant one too.
- **Skill upload (if available on your plan):** zip the skill folder and upload it
  under Claude.ai → Settings → Capabilities/Skills. It then triggers automatically
  from its `description`.
  ```
  zip -rq <skill-name>.zip <skill-name>
  ```

## Adding a new skill

1. Copy the template into a new kebab-case folder:
   ```
   cp -r _template my-new-skill
   ```
2. Fill in `my-new-skill/SKILL.md`.
3. Add a row to the **Skills** table above.

## Authoring conventions

Distilled from building the skills here:

- **Trigger on meaning, not keywords.** The `description` and instructions should
  match what a clause/request *means*, however it's worded — and notice what's
  *missing*, not just what's present.
- **Separate structure from substance.** Judge what the skill can judge; hand
  deal-specific substance to a human and say so explicitly.
- **Be honest about limits.** Never return a false "all clear" on something the
  skill couldn't actually assess. Escalate instead of guessing.
- **Match output to the task.** Different jobs deserve different output shapes
  (a fast verdict vs. a detailed review vs. a summary).
- **Keep `SKILL.md` lean; push depth into supporting files** loaded on demand.
