---
name: jj prev
description: Use when the agent needs to move the jj working copy to a parent revision (navigate backward in history)
---

# jj prev

## Usage
```
jj prev [OPTIONS] [OFFSET]
```

Moves the working copy to a parent revision (toward ancestors).

### Common Options
- `[OFFSET]` - Number of generations to move back (default: 1)
- `-e, --edit` - Edit the destination revision instead of creating a new change on top
- `--conflict` - Jump to the previous conflicted ancestor

## Key Concepts
- Moves "backward" in history (toward parents/ancestors)
- By default, creates new change on top of destination
- With `-e`, edits the destination directly
- Complement of `jj next`

## Common Patterns
```bash
# Move to parent
jj prev

# Move to parent and edit it directly
jj prev -e

# Move back 2 generations (to grandparent)
jj prev 2

# Move to grandparent and edit
jj prev 2 -e

# Jump to previous conflicted commit
jj prev --conflict
```

## Behavior Details
- If there are multiple parents (merge commit), jj will prompt you to choose
- Without `-e`: Creates new empty change as child of destination
- With `-e`: Makes destination the working copy directly

## Navigation Workflow
```bash
# Go back to fix something
jj prev -e     # Edit parent directly

# Or create a "fix" commit
jj prev        # New change on top of parent
# make fix
jj squash      # Fold fix into parent
jj next        # Return forward
```

## Comparison: prev vs edit
- `jj prev -e` = Navigate to parent and edit
- `jj edit @-` = Same result, different syntax
- `jj prev` = Create new change, parent becomes grandparent

## Guidelines
Show the log after to confirm the new position in history.
