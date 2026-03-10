---
name: jj show
description: Use when the agent needs to display a jj commit's description and diff, or inspect changes introduced by a specific revision
---

# jj show

## Usage
```
jj show [OPTIONS] [REVISION]
```

Shows the description and changes of a revision.

### Common Options
- `[REVISION]` - Revision to show (default: `@`)
- `-s, --summary` - Show only file names changed, not full diff
- `--stat` - Show a histogram of changes
- `--git` - Show Git-format diff
- `--color-words` - Word-level diff highlighting
- `-T, --template <TEMPLATE>` - Custom template for the header
- `--tool <TOOL>` - Use external diff tool

## Key Concepts
- Combines commit info + diff in one view
- Similar to `git show`
- Shows changes introduced BY the revision (vs its parent)

## Common Patterns
```bash
# Show current working copy changes
jj show

# Show parent commit
jj show @-

# Show specific revision
jj show abc123

# Show only which files changed
jj show -s

# Show with statistics
jj show --stat

# Show commit at a bookmark
jj show main
```

## Output Includes
1. Commit ID and change ID
2. Author and timestamp
3. Description (commit message)
4. Full diff of changes

## Comparison with Other Commands
- `jj show` = Full commit details + diff
- `jj log -p -r X` = Same diff, but in log format
- `jj diff -r X` = Just the diff, no commit info

## Guidelines
If the diff is very large, consider using `-s` for a summary first, then showing specific files.
