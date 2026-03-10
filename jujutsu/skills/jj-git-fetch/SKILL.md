---
name: jj git fetch
description: Use when the agent needs to fetch changes from a Git remote into a jj repository
---

# jj git fetch

## Usage
```
jj git fetch [OPTIONS]
```

Fetches changes from Git remote(s).

### Common Options
- `-b, --branch <BRANCH>` - Fetch only this branch/bookmark
- `--all-remotes` - Fetch from all remotes
- `--remote <REMOTE>` - Fetch from specific remote (default: origin)

## Key Concepts
- Fetches Git refs and converts to jj bookmarks
- Remote bookmarks appear as `<bookmark>@<remote>` (e.g., `main@origin`)
- Local bookmarks are NOT automatically updated
- Use `jj rebase` to update your work after fetching

## Common Patterns
```bash
# Fetch from default remote (origin)
jj git fetch

# Fetch from all configured remotes
jj git fetch --all-remotes

# Fetch specific branch only
jj git fetch -b main

# Fetch from specific remote
jj git fetch --remote upstream
```

## After Fetching
Common workflows after fetch:

```bash
# See what was fetched
jj log -r 'remote_bookmarks()'

# Update your branch to latest remote
jj rebase -d main@origin

# See difference between local and remote
jj log -r 'main..main@origin'

# Fast-forward local bookmark to remote
jj bookmark set main -r main@origin
```

## Remote Bookmark Naming
- `main@origin` - The 'main' branch on 'origin' remote
- `feature@upstream` - The 'feature' branch on 'upstream' remote
- `trunk()` - Shortcut for the main remote branch

## Guidelines
After fetching, show relevant log output to display what was fetched. Suggest next steps like rebasing if appropriate.
