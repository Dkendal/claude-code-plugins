---
name: jj op
description: Use when the agent needs to view operation history, restore repository to a previous state, or recover from mistakes in jj
---

# jj op (operation)

## Usage
```
jj op <COMMAND> [OPTIONS]
```

Manages the operation log - jj's built-in time machine for your repository.

### Subcommands
- `log` - Show operation history
- `restore` - Restore repo to a previous operation state
- `diff` - Show changes between operations
- `abandon` - Abandon old operations (cleanup)

## Key Concepts
- Every change to the repo creates an operation
- Operations form an immutable history
- You can restore to any previous operation
- This enables fearless experimentation

## Common Patterns

### View operation log
```bash
# Show recent operations
jj op log

# Show more operations
jj op log -n 20

# Show specific operation details
jj op show abc123
```

### Restore to previous state
```bash
# Restore to a specific operation
jj op log  # Find the operation ID
jj op restore abc123

# Same as undo, but can go further back
jj op restore @-  # Previous operation
jj op restore @-3  # Three operations ago
```

### Compare operations
```bash
# Show what changed between operations
jj op diff --from abc123 --to def456

# Show what the last operation changed
jj op diff --from @- --to @
```

### Clean up old operations
```bash
# Abandon operations older than 2 weeks
jj op abandon '..@-' --older-than '2 weeks'
```

## Operation Log Output
Each entry shows:
- Operation ID (use for restore/diff)
- Timestamp
- User
- Tags (what kind of operation)
- Description of what changed

## Recovery Scenarios

### Recover from bad rebase
```bash
jj op log  # Find operation before rebase
jj op restore <id>
```

### See what a command did
```bash
jj op diff --from @- --to @
```

### Recover deleted bookmark
```bash
jj op log  # Find when bookmark existed
jj op restore <id>
```

## Comparison with Git
- `jj op log` ≈ `git reflog` but for ALL operations
- `jj op restore` ≈ `git reset` to reflog entry
- Much more comprehensive than Git's reflog

## Guidelines
For `log`, show recent operations. For `restore`, confirm with the user before restoring. For `diff`, show what changed between operations.
