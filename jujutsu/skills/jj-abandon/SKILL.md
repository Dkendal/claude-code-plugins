---
name: jj abandon
description: Use when the agent needs to abandon (remove) jj revisions from history
---

# jj abandon

## Usage
```
jj abandon [OPTIONS] [REVISIONS]...
```

Abandons the specified revision(s). The changes are removed and descendants are rebased onto the parent.

### Common Options
- `[REVISIONS]` - Revisions to abandon (default: `@`)
- `-r, --revision <REVSET>` - Alternative way to specify revisions
- `--restore-descendants` - Restore descendants that would become empty

## Key Concepts
- Abandoning removes changes from history
- Descendants are automatically rebased onto the abandoned commit's parent
- Different from `git reset` - jj abandon is cleaner
- You can recover abandoned commits with `jj undo`

## Common Patterns
```bash
# Abandon the working copy changes
jj abandon

# Abandon a specific revision
jj abandon abc123

# Abandon the parent commit
jj abandon @-

# Abandon multiple revisions
jj abandon abc123 def456

# Abandon a range of commits
jj abandon 'abc123::def456'

# Abandon all empty commits
jj abandon 'empty()'
```

## Safety
- Abandoned commits can be recovered with `jj undo`
- You can see abandoned commits in `jj op log`
- Descendants are preserved by rebasing

## Comparison with Git
- `jj abandon @` is like `git reset --hard HEAD^` but safer
- `jj abandon` + `jj undo` = safe experimentation

## Guidelines
Warn the user if abandoning multiple commits. Show the log after to confirm the changes.
