---
name: jj new
description: Use when the agent needs to create a new empty jj change, start fresh work, or create merge commits
---

# jj new

## Usage
```
jj new [OPTIONS] [REVISIONS]...
```

Creates a new, empty change as a child of the specified revision(s). The working copy (`@`) moves to the new change.

### Common Options
- `[REVISIONS]` - Parent revision(s) for the new change (default: `@`)
- `-m, --message <MESSAGE>` - Description for the new change
- `-A, --insert-after` - Insert after the given commit(s)
- `-B, --insert-before` - Insert before the given commit(s)
- `--no-edit` - Don't move working copy to new change

## Key Concepts
- This is similar to starting fresh work in Git
- The new change starts empty - your next edits go into it
- Creating with multiple parents makes a merge commit
- Use this to "save" current work and start fresh

## Common Patterns
```bash
# Create new empty change on top of current
jj new

# Create with a description
jj new -m "Start working on feature X"

# Create new change on top of specific revision
jj new main

# Create merge commit with multiple parents
jj new branch1 branch2 -m "Merge branches"

# Insert a new change between two commits
jj new --insert-before @

# Create new change but stay on current
jj new --no-edit
```

## Workflow Note
In jj, `jj new` is like "committing" your current work:
1. Your changes are already in `@`
2. `jj new` creates empty child, moving `@` there
3. Previous changes stay in `@-`

This replaces `git add && git commit`.

## Guidelines
After creating, show the new status to confirm the change was created.
