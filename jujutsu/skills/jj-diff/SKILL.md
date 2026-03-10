---
name: jj diff
description: Use when the agent needs to compare file contents between jj revisions or view working copy changes
---

# jj diff

## Usage
```
jj diff [OPTIONS] [PATHS]...
```

Shows differences in files between revisions.

**IMPORTANT: Always use the `--git` flag when running `jj diff`.** The default diff output format is not reliably parseable. The `--git` flag produces standard Git-format diffs that are well-understood.

### Common Options
- `-r, --revision <REVSET>` - Show changes in this revision (compare with parent)
- `--from <REVSET>` - Start revision for comparison
- `--to <REVSET>` - End revision for comparison (default: `@`)
- `-s, --summary` - Show only file names, not content diff
- `--stat` - Show a histogram of changes
- `--git` - **REQUIRED.** Show Git-format diff
- `--color-words` - Show word-level diff with colors
- `--tool <TOOL>` - Use external diff tool

## Common Patterns
```bash
# Show changes in working copy (vs parent)
jj diff --git

# Show changes in a specific revision
jj diff --git -r @-

# Compare two revisions
jj diff --git --from main --to @

# Show only which files changed
jj diff -s

# Show diff for specific file
jj diff --git src/lib.rs

# Show changes between trunk and working copy
jj diff --git --from trunk() --to @

# Use external diff tool
jj diff --tool meld
```

## Understanding Revision Comparison
- `jj diff` alone shows `@-` → `@` (parent to working copy)
- `jj diff -r X` shows changes introduced BY revision X (its parent → X)
- `jj diff --from A --to B` shows A → B

## Guidelines
Always use `--git` flag for machine-readable output. For large diffs, consider using `-s` first to get a summary, then showing specific files.
