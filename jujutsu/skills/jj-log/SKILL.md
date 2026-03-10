---
name: jj log
description: Use when the agent needs to view jj revision history, find commits, or explore the commit graph
---

# jj log

## Usage
```
jj log [OPTIONS] [PATHS]...
```

Shows the revision history as a graph.

### Common Options
- `-r, --revisions <REVSET>` - Which revisions to show (default: `@ | ancestors(immutable_heads().., 2) | trunk()`)
- `-n, --limit <LIMIT>` - Maximum number of revisions to show
- `-p, --patch` - Show diffs for each revision
- `-s, --summary` - Show one-line summary per file changed
- `--no-graph` - Don't show the graph, faster for large logs
- `-T, --template <TEMPLATE>` - Custom output template

## Revset Examples
- `@` - Working copy commit
- `@-` - Parent of working copy
- `@--` or `@-2` - Grandparent
- `::@` - All ancestors of working copy
- `@::` - All descendants of working copy
- `bookmarks()` - All bookmarked commits
- `trunk()` - Main/master bookmark
- `heads(all())` - All head commits
- `description(pattern)` - Commits matching description

## Common Patterns
```bash
# Show recent history (default view)
jj log

# Show last 10 commits
jj log -n 10

# Show all commits on current branch
jj log -r '::@'

# Show commits with diffs
jj log -p -n 3

# Show commits affecting a file
jj log src/main.rs

# Show all bookmarks
jj log -r 'bookmarks()'

# Show commits between trunk and working copy
jj log -r 'trunk()..@'
```

## Guidelines
Default to showing a reasonable number of commits if no limit specified. Summarize the history if the output is long.
