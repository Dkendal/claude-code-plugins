---
name: jj next
description: Use when the agent needs to move the jj working copy to a child revision (navigate forward in history)
---

# jj next

## Usage
```
jj next [OPTIONS] [OFFSET]
```

Moves the working copy to a child revision (toward descendants).

### Common Options
- `[OFFSET]` - Number of generations to move (default: 1)
- `-e, --edit` - Edit the destination revision instead of creating a new change on top
- `--conflict` - Jump to the next conflicted descendant

## Key Concepts
- Moves "forward" in history (toward children/descendants)
- By default, creates new change on top of destination
- With `-e`, edits the destination directly
- Complement of `jj prev`

## Common Patterns
```bash
# Move to direct child
jj next

# Move to direct child and edit it
jj next -e

# Move forward 2 generations
jj next 2

# Jump to next conflicted commit
jj next --conflict
```

## Behavior Details
- If there are multiple children, jj will prompt you to choose
- Without `-e`: Creates new empty change as child of destination
- With `-e`: Makes destination the working copy directly

## Navigation Workflow
```bash
# Typical history navigation
jj prev -e    # Go back to edit something
# make changes
jj next       # Return to where you were
```

## Comparison with jj edit
- `jj next -e` = Navigate to child and edit
- `jj edit <child>` = Edit specific revision
- `jj next` = Create new change on top of child

## Guidelines
If there are multiple children, the command will prompt for selection. Show the log after to confirm the new position.
