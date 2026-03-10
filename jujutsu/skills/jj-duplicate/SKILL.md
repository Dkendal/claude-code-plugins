---
name: jj duplicate
description: Use when the agent needs to create copies of jj revisions (similar to cherry-pick)
---

# jj duplicate

## Usage
```
jj duplicate [OPTIONS] [REVISIONS]...
```

Creates new commits with the same content as the specified revisions. The originals remain unchanged.

### Common Options
- `[REVISIONS]` - Revisions to duplicate (default: `@`)
- `-d, --destination <REVSET>` - Parent(s) for the duplicated commits

## Key Concepts
- Creates copies, doesn't move originals
- New commits get new change IDs
- Useful for "cherry-picking" without moving
- Duplicated commits are independent of originals

## Common Patterns
```bash
# Duplicate the working copy commit
jj duplicate

# Duplicate a specific commit
jj duplicate abc123

# Duplicate multiple commits
jj duplicate abc123 def456

# Duplicate onto a different parent
jj duplicate abc123 -d main

# Duplicate a range of commits
jj duplicate 'abc123::def456'
```

## Use Cases
1. **Cherry-pick to another branch**: Duplicate commit onto target branch
2. **Experiment safely**: Duplicate before making risky changes
3. **Create parallel variations**: Duplicate to try different approaches

## Comparison with Git
- `jj duplicate X -d Y` ≈ `git cherry-pick X` (onto branch Y)
- But jj duplicate keeps the original, cherry-pick "moves" in a sense

## Workflow: Cherry-pick Style
```bash
# Duplicate feature commit onto main
jj duplicate feature-commit -d main
# Now you have the same changes on main
```

## Guidelines
Show the log after to display both the original and duplicated commits.
