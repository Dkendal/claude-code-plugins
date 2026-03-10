---
name: jj edit
description: Use when the agent needs to set a specific jj revision as the working copy to modify it directly
---

# jj edit

## Usage
```
jj edit <REVISION>
```

Sets the specified revision as the working copy (`@`). Any changes you make will modify that revision directly.

### Common Options
- `<REVISION>` - The revision to edit (required)

## Key Concepts
- Changes the working copy to point to an existing commit
- Your file changes will now modify that commit
- Different from `jj new <rev>` which creates a new child
- Useful for going back to fix or update previous commits

## Common Patterns
```bash
# Edit the parent commit
jj edit @-

# Edit a specific commit by change ID
jj edit abc123

# Edit the commit at a bookmark
jj edit main

# Edit grandparent
jj edit @--
```

## Comparison with Similar Commands
- `jj edit X` - Makes X the working copy (changes go INTO X)
- `jj new X` - Creates new child of X (changes go into NEW commit)
- `jj next/prev` - Navigate and optionally edit

## Workflow: Fixing Earlier Commits
1. `jj log` to find the commit to fix
2. `jj edit <commit>` to make it the working copy
3. Make your changes
4. `jj new` or `jj next` to move forward again

## Warning
If the revision has descendants, editing it will cause them to be rebased. This is usually fine but be aware of it.

## Guidelines
Show the status and log after to confirm the working copy has changed.
