---
name: update-rebuild-recipe
description: Monthly backup sweep — refresh the Mac rebuild recipe (apps, Homebrew, settings), push all pending memory changes, and sync claude.ai skill edits back into the skills monorepo. Use when the user asks to update their rebuild recipe, machine inventory, or computer-setup backup, says "run my backup sweep", or when run as a scheduled task. Claude Code only (needs local filesystem access).
---

# /update-rebuild-recipe — Monthly backup sweep

Three jobs, in order: refresh the machine inventory, push memory, sync skills.
The rebuild recipe lives in the private memory-backup git repo at
`~/.claude/projects/`, under `machine/`. The skills monorepo is
`~/claude-skills` (PUBLIC on GitHub — mind the unattended rule below).

## 1. Refresh the machine inventory

1. `brew bundle dump --file=$HOME/.claude/projects/machine/Brewfile --force`
2. Re-scan `/Applications` (strip `.app`), update the app list in
   `machine/rebuild-recipe.md` — add new apps, drop removed ones.
3. Re-capture settings if changed: wallpaper (compare current desktop picture
   with `machine/settings/wallpaper.jpg`), trackpad/dock defaults in
   `machine/settings/apply-settings.sh`.
4. Refresh dotfile copies in `machine/dotfiles/` — **always redact API keys
   and secrets** (grep for `sk-`, `key`, `token`, `secret` before staging).
5. Update the snapshot date in the recipe heading.

## 2. Push the memory repo

In `~/.claude/projects/`: `git add -A`, review `git status --short` (machine/
and */memory/ files only — never transcripts), commit
(`Backup sweep <date>`), push.

## 3. Sync skills (claude.ai → monorepo)

1. Find the freshest claude.ai skill cache under
   `~/Library/Application Support/Claude/local-agent-mode-sessions/skills-plugin/`
   (most recently modified session dir).
2. Diff each cached skill against `~/claude-skills` — including skills present
   in the cache but with no folder in the monorepo yet (brand new).
3. Apply updates to already-tracked skills, and copy in any brand-new ones,
   adding a row to the README table (name, one-line description, "Uploaded to
   claude.ai"). Commit, push.
4. Remind the user of the reverse direction if monorepo skills changed since
   their last claude.ai upload (they must re-zip + re-upload by hand).

## Unattended rule (scheduled runs)

The monorepo is public — Antoine has confirmed his skills never contain
sensitive content, so new skills sync automatically like updates do. Still:
- If a diff looks personal (names, keys, private context) despite that,
  skip it and flag it in the summary rather than pushing.
- Never commit secrets (API keys, tokens, passwords) regardless of source.

## Wrap-up

End with a short summary: apps added/removed, memory files pushed, skills
synced, anything flagged for Antoine.

## Notes

- Never commit secrets anywhere — passwords live in Keychain, keys get
  recreated at providers.
- If the machine or username differs from the recipe's, ask before
  overwriting — it may be a new computer restoring, not an update.
