---
name: sound-packs
description: List available Claude Code sound packs and switch between them by updating the afplay hook paths in settings.json
---

# Sound Packs

Manage Claude Code sound packs. Sound packs are collections of four audio files played by `afplay` hooks in `~/.claude/settings.json`.

## Sound Pack Location

All sound packs live in the `sounds/` directory of this repository (the current working directory).

Each pack is a subdirectory containing up to four files:
- `session-start.mp3` — played on `SessionStart`
- `notification.wav` — played on `Notification`
- `prompt-submit.mp3` — played on `UserPromptSubmit`
- `stop.wav` — played on `Stop`

## Listing Available Sound Packs

Use the Glob or Bash tool to list subdirectories under the sounds directory:

```bash
ls sounds/
```

Present the results as a numbered list so the user can choose easily.

## Switching Sound Packs

1. Read `~/.claude/settings.json`
2. Identify the four `afplay` command strings (one per hook: `SessionStart`, `Notification`, `UserPromptSubmit`, `Stop`)
3. Replace the pack name in each path with the new pack name, keeping the existing base path intact
4. Write the updated file back using the Edit tool — update all four commands

### Important notes
- Some packs use `.mp3` files or `.wav` — check what files actually exist in the target pack before writing paths (use Glob or Bash)
- Do not change anything else in `settings.json`
- After updating, confirm which pack is now active and list the four file paths that were set

## Example Interaction

User: `/sound-packs` or "switch to the mario sound pack"

1. List available packs (if user hasn't specified one)
2. Check files in the chosen pack to determine extension (`.wav` vs `.mp3`)
3. Update all four hook commands in `settings.json`
4. Confirm the change
