---
name: restore-mac
description: Set up a fresh Mac from the rebuild recipe in the private claude-memory repo — reinstall apps, command-line tools, dotfiles, fonts, skills, and memory. Use when the user says they have a new Mac / new computer, lost their laptop, or asks to "set up my new Mac" or "restore my computer". Claude Code only (needs local filesystem access).
---

# /restore-mac — Rebuild this Mac from the recipe

The recipe (data) lives in the private repo `github.com/antoinebernzrd/claude-memory`
under `machine/rebuild-recipe.md`. This skill is the procedure that applies it.

## Order of operations

1. **Get the recipe.** If `~/.claude/projects/machine/rebuild-recipe.md` doesn't
   exist yet: user signs into GitHub (`gh auth login` — they type credentials,
   not you), then clone `claude-memory` and restore its contents into
   `~/.claude/projects/` (git repo at that root — clone elsewhere and move the
   working tree + `.git` in, don't overwrite newer local memories if any exist).
2. **Read the recipe end to end.** It is the source of truth for what to
   install; this skill only defines the order and the rules below.
3. **Command-line layer first:** Homebrew, then `brew bundle` from
   `machine/Brewfile`, then Claude Code, Bun, git-lfs (per recipe §4).
4. **Dotfiles:** copy from `machine/dotfiles/` into `~` per recipe §5. Remind
   the user to insert a fresh OpenAI key (the stored copy is redacted).
5. **Apps:** install what can be automated (many recipe §3 apps exist as brew
   casks — `brew install --cask brave-browser docker notion obsidian raycast telegram anki github` etc.;
   check each with `brew search` first). For App Store apps (§2) and anything
   without a cask, list them for the user to install by hand.
6. **Fonts:** download Montserrat from Google Fonts into `~/Library/Fonts`.
7. **Skills:** clone `claude-skills`, symlink its skill folders into
   `~/.claude/skills/` per its README.
8. **Sign-ins last:** print the accounts checklist (recipe §1) for the user.

## Rules

- **Never type passwords, API keys, or payment details** — sign-ins and
  key creation are the user's job; give them the checklist and wait.
- **Ledger Live:** do not download from a search result — user must type
  ledger.com themselves (crypto wallet, phishing target).
- **Ask before overwriting** any file that already exists on the new machine.
- Work top to bottom, report progress per section, and end with a summary of
  what was installed vs. what's left for the user.
