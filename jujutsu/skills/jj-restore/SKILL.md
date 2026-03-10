---
name: jj restore
description: Use when the agent needs to restore file contents from another jj revision or discard working copy changes
---

# jj restore

## Usage
```
jj restore [OPTIONS] [PATHS]...
```

Restores files to their contents from another revision. By default, restores the working copy to match its parent.

### Common Options
- `--from <REVSET>` - Source revision (default: `@-`)
- `--to <REVSET>` - Target revision to modify (default: `@`)
- `-c, --changes-in <REVSET>` - Undo changes made in this revision
- `[PATHS]` - Specific paths to restore

## Key Concepts
- Restores file contents, not the whole commit
- Default behavior: undo working copy changes (restore from parent)
- Can restore specific files from any revision

## Common Patterns
```bash
# Discard all working copy changes (restore to parent state)
jj restore

# Restore specific file to parent version
jj restore src/main.rs

# Restore file from a specific revision
jj restore --from main src/config.rs

# Restore file from a specific commit
jj restore --from abc123 src/lib.rs

# Undo changes introduced by a specific commit
jj restore -c @-

# Restore working copy to match a specific revision entirely
jj restore --from main
```

## Comparison with Git
- `jj restore` ≈ `git checkout -- <files>`
- `jj restore --from X` ≈ `git checkout X -- <files>`
- `jj restore` (no args) ≈ `git checkout -- .`

## Use Cases
1. **Discard unwanted changes**: `jj restore <file>`
2. **Get file from another branch**: `jj restore --from main <file>`
3. **Revert a specific commit's changes**: `jj restore -c <commit>`
4. **Cherry-pick file content**: `jj restore --from feature-branch specific-file.rs`

## Guidelines
Warn if restoring without paths specified, as this affects all files. Show status after to confirm the restoration.
