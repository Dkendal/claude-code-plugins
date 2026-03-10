---
name: jj describe
description: Use when the agent needs to update or set the description (commit message) of a jj change
---

# jj describe

## Usage
```
jj describe [OPTIONS] [REVISIONS]...
```

Updates the description (commit message) of one or more revisions.

### Common Options
- `[REVISIONS]` - Revisions to describe (default: `@`)
- `-m, --message <MESSAGE>` - New description text
- `--stdin` - Read description from stdin
- `--reset-author` - Reset author to configured user

## Key Concepts
- Changes in jj are mutable by default
- You can update descriptions at any time
- Describing `@` is common before using `jj new`

## Common Patterns
```bash
# Set description for working copy
jj describe -m "Add user authentication"

# Update a specific revision's description
jj describe -m "Fix login bug" @-

# Describe multiple revisions at once
jj describe -m "Part of refactor" abc123 def456

# Multi-line description
jj describe -m "Summary line

Detailed explanation here.
More details."

# Clear description (set to empty)
jj describe -m ""
```

## Workflow Tips
- Describe changes early and update as you work
- Use conventional commit format if your team requires it
- The working copy (`@`) often has "(no description set)" initially

## Guidelines
If no message is provided and the user wants to describe the current change, ask what the description should be. Show the log entry after to confirm.
