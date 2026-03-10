---
name: jj split
description: Use when the agent needs to split a jj revision into two separate commits
---

# jj split

## Usage
```
jj split [OPTIONS] [PATHS]...
```

Splits a revision into two consecutive revisions. The first revision contains the selected changes, and the second contains the rest.

### Common Options
- `-r, --revision <REVSET>` - Revision to split (default: `@`)
- `-m, --message <MESSAGE>` - Description for the first part
- `-i, --interactive` - Interactively select changes for first part
- `[PATHS]` - Put changes to these paths in first revision
- `-p, --parallel` - Create siblings instead of parent-child

## Key Concepts
- Useful for breaking up commits that are too large
- Creates two commits: first with selected changes, second with remainder
- The original commit is replaced by the two new commits

## Common Patterns
```bash
# Split by selecting files for first commit
jj split src/feature.rs tests/feature_test.rs

# Split interactively (choose hunks)
jj split -i

# Split with message for first part
jj split -m "Refactor: extract helper function" src/helpers.rs

# Split a specific revision
jj split -r @- src/main.rs

# Split into parallel commits (siblings, not parent-child)
jj split -p src/a.rs src/b.rs
```

## Workflow: Cleaning Up History
1. You have a commit with multiple logical changes
2. `jj split -i` to interactively select first logical unit
3. Describe the second part with `jj describe`
4. Repeat if needed

## Guidelines
Note that `-i` requires terminal interaction. After splitting, show the log to display the resulting commits.
