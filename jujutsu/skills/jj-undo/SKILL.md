---
name: jj undo
description: Use when the agent needs to undo a jj operation and restore the repository to its previous state
---

# jj undo

## Usage
```
jj undo [OPTIONS] [OPERATION]
```

Undoes a jj operation, restoring the repository to its previous state.

### Common Options
- `[OPERATION]` - Operation to undo (default: latest)
- `--what <WHAT>` - What to restore: `repo`, `remote-tracking`

## Key Concepts
- Every jj command that modifies the repo is an "operation"
- Operations are recorded in an operation log
- `jj undo` reverts the repo to before an operation
- This is incredibly powerful for recovery

## Common Patterns
```bash
# Undo the last operation
jj undo

# See operation history first
jj op log

# Undo a specific operation
jj op log  # Find the operation ID
jj undo abc123def

# Multiple undos (undo twice)
jj undo
jj undo
```

## What Can Be Undone
- Commits, amends, squashes
- Rebases
- Bookmark changes
- Abandons
- Almost any repository modification

## Operation Log
Use `jj op log` to see the history:
```bash
jj op log -n 10  # Recent operations
```

Each operation shows:
- Operation ID
- Time
- User
- What changed

## Recovery Workflows

### Undo accidental abandon
```bash
jj undo  # Brings back the abandoned commit
```

### Undo bad rebase
```bash
jj undo  # Restore previous structure
```

### Go back multiple steps
```bash
jj op log -n 10  # Find where things were good
jj undo <operation-id>  # Restore to that point
```

## Comparison with Git
- `jj undo` ≈ `git reflog` + `git reset`, but much simpler
- Every operation is automatically logged
- No need to remember commit SHAs

## Guidelines
Show the status and/or log after to confirm what was restored.
