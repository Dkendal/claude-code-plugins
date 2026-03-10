---
name: jj git push
description: Use when the agent needs to push jj bookmarks or commits to a Git remote
---

# jj git push

## Usage
```
jj git push [OPTIONS]
```

Pushes bookmarks to a Git remote.

### Common Options
- `-b, --bookmark <BOOKMARK>` - Push specific bookmark(s)
- `--all` - Push all bookmarks
- `-c, --change <REVSET>` - Push this commit by creating/updating a bookmark
- `--deleted` - Push deleted bookmarks
- `-r, --revisions <REVSET>` - Push bookmarks pointing to these revisions
- `--remote <REMOTE>` - Target remote (default: origin)
- `--dry-run` - Show what would be pushed without actually pushing

## Key Concepts
- jj bookmarks = Git branches
- Only bookmarks can be pushed (not arbitrary commits)
- Use `-c` to push a commit by auto-creating a bookmark
- Remote tracking bookmarks are updated automatically

## Common Patterns
```bash
# Push all updated bookmarks
jj git push

# Push specific bookmark
jj git push -b main

# Push multiple bookmarks
jj git push -b feature-a -b feature-b

# Push current commit (creates bookmark if needed)
jj git push -c @

# Push with auto-generated bookmark name
jj git push -c abc123

# See what would be pushed
jj git push --dry-run

# Push all bookmarks including new ones
jj git push --all

# Push to specific remote
jj git push --remote upstream -b main
```

## Push by Change (-c)
When using `-c`:
1. If commit has a bookmark, pushes that bookmark
2. If no bookmark, creates one named `push-<change_id_prefix>`
3. Very convenient for quick sharing

## Troubleshooting
- "Non-fast-forward" error: Remote has commits you don't have. Fetch first.
- "No bookmarks to push": Create a bookmark or use `-c`
- To force push: Use `-b <bookmark> --force` (careful!)

## Guidelines
Default to `--dry-run` first if uncertain about what will be pushed. Report what was pushed and any errors.
