---
name: jj bookmark
description: Use when the agent needs to manage jj bookmarks (the equivalent of Git branches)
---

# jj bookmark

## Usage
```
jj bookmark <COMMAND> [OPTIONS]
```

Manages bookmarks (equivalent to Git branches).

### Subcommands
- `create` - Create a new bookmark
- `delete` - Delete a bookmark
- `list` - List bookmarks
- `move` - Move a bookmark to another revision
- `rename` - Rename a bookmark
- `set` - Set a bookmark to a revision (create or move)
- `track` - Start tracking a remote bookmark
- `untrack` - Stop tracking a remote bookmark

## Key Concepts
- Bookmarks in jj = Branches in Git
- Bookmarks point to specific revisions
- Remote bookmarks: `name@remote` (e.g., `main@origin`)
- Local bookmarks move automatically when you amend/rebase

## Common Patterns

### Create bookmark
```bash
# Create bookmark at current revision
jj bookmark create feature-x

# Create bookmark at specific revision
jj bookmark create feature-x -r abc123

# Shorthand: set creates if doesn't exist
jj bookmark set feature-x
```

### List bookmarks
```bash
# List all bookmarks
jj bookmark list

# List with full commit info
jj bookmark list -a

# List bookmarks matching pattern
jj bookmark list 'glob:feature-*'
```

### Move bookmark
```bash
# Move bookmark to current revision
jj bookmark move main

# Move bookmark to specific revision
jj bookmark move main -r abc123

# Set is often clearer (same result)
jj bookmark set main -r @
```

### Delete bookmark
```bash
# Delete local bookmark
jj bookmark delete feature-x

# Delete multiple
jj bookmark delete feature-a feature-b
```

### Track remote bookmarks
```bash
# Start tracking a remote bookmark
jj bookmark track main@origin

# Stop tracking
jj bookmark untrack main@origin
```

## Bookmark vs Git Branch
| Git | jj |
|-----|-----|
| `git branch X` | `jj bookmark create X` |
| `git branch -d X` | `jj bookmark delete X` |
| `git branch -m X Y` | `jj bookmark rename X Y` |
| `git checkout -b X` | `jj bookmark create X && jj new X` |

## Guidelines
Show the bookmark list after modifications to confirm the change.
