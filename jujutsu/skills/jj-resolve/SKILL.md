---
name: jj resolve
description: Use when the agent needs to resolve merge conflicts in a jj repository
---

# jj resolve

## Usage
```
jj resolve [OPTIONS] [PATHS]...
```

Resolves merge conflicts in the working copy or specified revision.

### Common Options
- `-r, --revision <REVSET>` - Revision with conflicts to resolve (default: `@`)
- `-l, --list` - List conflicted files instead of resolving
- `--tool <TOOL>` - Use specific merge tool (e.g., meld, vimdiff)
- `[PATHS]` - Specific files to resolve

## Key Concepts
- Conflicts occur during rebases and merges
- jj tracks conflicts as first-class citizens
- Conflicted files contain conflict markers
- Use external merge tools for easier resolution

## Common Patterns
```bash
# List all conflicts
jj resolve -l

# Resolve all conflicts with default tool
jj resolve

# Resolve specific file
jj resolve src/main.rs

# Use specific merge tool
jj resolve --tool meld
jj resolve --tool vimdiff
jj resolve --tool vscode

# Resolve conflicts in a different revision
jj resolve -r abc123
```

## Conflict Markers
Conflicted files contain markers like:
```
<<<<<<< Conflict 1 of 1
%%%%%%% Changes from base to side #1
-old line
+side 1 line
+++++++ Contents of side #2
side 2 line
>>>>>>> Conflict 1 of 1 ends
```

## Resolution Workflow

### Using merge tool
```bash
jj resolve --tool meld  # Opens visual merge tool
# Resolve in the tool, save, and close
# jj automatically updates the revision
```

### Manual resolution
1. Edit the conflicted file directly
2. Remove conflict markers
3. Keep the desired content
4. The conflict auto-resolves when markers are removed

### After resolving
```bash
jj status  # Should show no conflicts
jj diff    # Review the resolution
```

## Common Merge Tools
- `meld` - Visual diff/merge (GTK)
- `vimdiff` - Vim-based
- `vscode` - VS Code
- `kdiff3` - KDE merge tool

Configure default: `jj config set --user ui.merge-editor "meld"`

## Guidelines
First list conflicts with `-l` to understand the scope. Then help resolve them using the specified tool or by showing the conflicted content for manual resolution.
