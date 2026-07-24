---
name: update-rebuild-recipe
description: Refresh the Mac rebuild recipe — re-scan installed apps and Homebrew packages, update the machine inventory in the private memory-backup repo, commit and push. Use when the user asks to update their rebuild recipe, machine inventory, or computer-setup backup, or mentions having installed/removed notable apps. Claude Code only (needs local filesystem access).
---

# /update-rebuild-recipe — Refresh the machine inventory

The rebuild recipe is the "lost my laptop" recovery sheet: accounts to sign into,
apps to reinstall, and restore steps. It lives in the private memory-backup git
repo at `~/.claude/projects/`, under `machine/`.

## Steps

1. **Refresh the Homebrew list:**
   ```
   brew bundle dump --file=$HOME/.claude/projects/machine/Brewfile --force
   ```
2. **Re-scan installed apps:** list `/Applications` (strip `.app`), compare with
   the app list in `machine/rebuild-recipe.md`, and update it — add new apps,
   drop removed ones.
3. **Sanity-check the rest of the recipe:** accounts and repo list still
   accurate? (Cross-check the skills-organization memory if unsure.) Update the
   snapshot date in the heading.
4. **Commit and push** in `~/.claude/projects/` with a short message like
   `Refresh machine inventory`.
5. **Report** what changed (apps added/removed) in one or two sentences.

## Notes

- Never add secrets (keys, passwords, tokens) to the recipe — it's for
  reinstalling, not authenticating; passwords live in Keychain.
- If the machine or username differs from the recipe's, ask before overwriting —
  it may be a new computer restoring from the old recipe, not an update.
