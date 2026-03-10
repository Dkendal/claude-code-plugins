---
name: jj status
description: Use when the agent needs to check the current state of a jj working copy, including modified, added, and conflicted files
---

# jj status

## Usage
```
jj status [OPTIONS] [PATHS]...
```

Shows the working copy's current status compared to its parent(s):
- Modified files
- Added files
- Removed files
- Conflicted files

### Common Options
- `[PATHS]` - Restrict output to specific paths

## Key Concepts
- In jj, the working copy is always a commit (`@`)
- There's no staging area - all changes are automatically tracked
- The status shows changes between `@` and `@-` (parent)

## Common Patterns
```bash
# Show status of entire repo
jj status

# Show status of specific file/directory
jj status src/

# Abbreviated form
jj st
```

## Guidelines
If there are conflicts, mention that they need to be resolved with `jj resolve`.
