---
name: jj squash
description: Use when the agent needs to move changes into a parent revision or amend a jj commit (equivalent to git commit --amend)
---

# jj squash

## Usage
```
jj squash [OPTIONS] [PATHS]...
```

Moves changes from one revision into another. By default, moves all changes from the working copy (`@`) into its parent (`@-`).

### Common Options
- `--from <REVSET>` - Source revision (default: `@`)
- `--into <REVSET>` - Destination revision (default: parent of source)
- `-r, --revision <REVSET>` - Shorthand for `--from`
- `-m, --message <MESSAGE>` - New description for destination
- `-i, --interactive` - Interactively select changes to squash
- `-u, --use-destination-message` - Keep destination's message
- `[PATHS]` - Only squash changes to these paths

## Key Concepts
- This is jj's equivalent to `git commit --amend`
- Moves changes from one commit into another
- The source commit becomes empty (and may be abandoned)
- Very useful for building up clean commits

## Common Patterns
```bash
# Amend parent with all working copy changes (most common)
jj squash

# Amend with a new message
jj squash -m "Updated implementation"

# Squash only specific files into parent
jj squash src/main.rs

# Interactively select what to squash
jj squash -i

# Squash a specific revision into its parent
jj squash --from @--

# Squash into a non-parent revision
jj squash --from @ --into abc123

# Keep the destination's existing message
jj squash -u
```

## Workflow: Building Clean Commits
1. Make changes (they're in `@`)
2. `jj squash` to fold into parent
3. Repeat until parent is complete
4. `jj new` to start next logical change

## Guidelines
After squashing, show the log to confirm the changes were moved. Note that interactive mode (`-i`) requires terminal interaction.
