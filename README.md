# Claude Code Plugins

A collection of [Claude Code](https://docs.anthropic.com/en/docs/claude-code) plugins by [@Dkendal](https://github.com/Dkendal).

## Plugins

### Jujutsu (`jj`)

Comprehensive skills and commands for the [Jujutsu](https://martinvonz.github.io/jj/) version control system.

**23 skills** covering the full jj workflow:

| Category | Skills |
|---|---|
| Core | `jj-new`, `jj-edit`, `jj-describe`, `jj-show` |
| Navigation | `jj-log`, `jj-next`, `jj-prev`, `jj-status` |
| Changes | `jj-commit`, `jj-squash`, `jj-split`, `jj-rebase` |
| Files | `jj-diff`, `jj-restore`, `jj-duplicate`, `jj-abandon` |
| Bookmarks | `jj-bookmark` |
| Conflicts | `jj-resolve` |
| Git integration | `jj-git-clone`, `jj-git-fetch`, `jj-git-push` |
| Recovery | `jj-undo`, `jj-op` |

**Commands:**

- `/commit` — Analyze working copy changes, compose a commit message, and commit via `jj commit`

## Installation

Add this plugin to your Claude Code configuration:

```sh
claude plugin add Dkendal/claude-plugins
```

## License

MIT
