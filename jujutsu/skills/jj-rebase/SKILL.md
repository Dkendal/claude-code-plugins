---
name: jj rebase
description: Use when the agent needs to move jj revisions to different parent(s), rebase branches, or reorder commits
---

# jj rebase

## Usage
```
jj rebase [OPTIONS]
```

Moves one or more revisions to a new parent. This is one of jj's most powerful commands.

### Common Options
- `-d, --destination <REVSET>` - New parent(s) for rebased commits
- `-s, --source <REVSET>` - Rebase this commit and its descendants
- `-b, --branch <REVSET>` - Rebase entire branch containing this commit
- `-r, --revisions <REVSET>` - Rebase only these specific revisions
- `--skip-emptied` - Skip commits that become empty after rebase

## Mode Differences
- `-s` (source): Moves commit AND all descendants
- `-b` (branch): Moves all commits from branch root
- `-r` (revisions): Moves only specified commits (children stay behind)

## Common Patterns
```bash
# Rebase current commit onto main
jj rebase -d main

# Rebase entire branch onto trunk
jj rebase -b @ -d trunk()

# Rebase specific commit and descendants onto target
jj rebase -s abc123 -d main

# Rebase just one commit (children stay in place)
jj rebase -r @- -d main

# Rebase onto multiple parents (create merge)
jj rebase -s @ -d branch1 -d branch2

# Rebase after fetching upstream changes
jj rebase -d 'trunk()'
```

## Common Workflows

### Update branch with latest main
```bash
jj git fetch
jj rebase -d main@origin
```

### Move commit to different position
```bash
jj rebase -r abc123 -d @
```

### Reorder commits
```bash
jj rebase -r @- -d @  # Swap current and parent
```

## Conflict Handling
If conflicts occur:
1. Resolve with `jj resolve`
2. The rebase continues automatically
3. Use `jj undo` to abort

## Guidelines
Always require a `-d` destination. Show the log after to visualize the new structure. If conflicts occur, inform the user about `jj resolve`.
