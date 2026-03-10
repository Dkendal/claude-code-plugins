---
name: jj git clone
description: Use when the agent needs to clone a Git repository into a new jj repository
---

# jj git clone

## Usage
```
jj git clone [OPTIONS] <SOURCE> [DESTINATION]
```

Clones a Git repository and creates a jj repo.

### Common Options
- `<SOURCE>` - Git repository URL or path
- `[DESTINATION]` - Directory name (default: derived from URL)
- `--colocate` - Create a repo colocated with the Git repo
- `--depth <DEPTH>` - Shallow clone with limited history

## Key Concepts
- Creates a jj repository backed by Git
- Can work alongside existing Git tools with `--colocate`
- All Git history is imported as jj revisions

## Common Patterns
```bash
# Clone a repository
jj git clone https://github.com/user/repo.git

# Clone to specific directory
jj git clone https://github.com/user/repo.git my-project

# Clone colocated (keeps .git, allows git commands)
jj git clone --colocate https://github.com/user/repo.git

# Shallow clone for faster download
jj git clone --depth 1 https://github.com/user/repo.git

# Clone from local path
jj git clone /path/to/other/repo
```

## Colocated vs Non-colocated

### Non-colocated (default)
- Pure jj repository
- Git data stored in `.jj/repo/store/git`
- Cannot use git commands directly

### Colocated (`--colocate`)
- Both `.jj` and `.git` directories
- Can use both jj and git commands
- Good for gradual migration or team compatibility
- Run `jj git export` to sync jj changes to git

## After Cloning
```bash
cd my-project
jj log              # See history
jj status           # Working copy status
jj bookmark list    # See branches (bookmarks)
```

## Guidelines
Recommend `--colocate` if the user might want to use git commands too. After cloning, show the initial status and suggest next steps.
