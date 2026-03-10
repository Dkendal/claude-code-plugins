---
name: jj commit
description: Use when the agent needs to finalize a jj change by setting its description and creating a new empty change on top
---

# jj commit

## Usage
```
jj commit [OPTIONS] [PATHS]...
```

Updates the working copy's description and creates a new empty change on top. This is a convenience command combining `jj describe` + `jj new`.

### Common Options
- `-m, --message <MESSAGE>` - Description for the current change
- `-i, --interactive` - Interactively select changes to include
- `[PATHS]` - Only commit changes to these paths (rest stay in new working copy)
- `--reset-author` - Reset author to configured user

## Key Concepts
- `jj commit` is the closest to `git commit`
- It finalizes the current change and moves to a new empty one
- Unlike git, changes are already tracked - this just "closes" the current change

## Common Patterns
```bash
# Commit current changes with message
jj commit -m "Add new feature"

# Commit only specific files
jj commit -m "Fix bug" src/bug.rs

# Interactively select what to commit
jj commit -i -m "Partial changes"

# Multi-line commit message
jj commit -m "Summary

Detailed description here."
```

## Comparison with Other Commands
- `jj commit -m "msg"` = `jj describe -m "msg" && jj new`
- `jj squash` = amend parent (like git commit --amend)
- `jj new` = create new change without describing current

## Guidelines
If no message is provided, ask the user what the commit message should be. Show the log after to confirm the commit was created.
