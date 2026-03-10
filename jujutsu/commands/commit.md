---
name: commit
description: Commit the current jj changes with an auto-generated or provided message
allowed-tools: Bash(jj *)
---

# Commit Current Changes

## Steps

1. Check the current state:
   ```bash
   jj status
   jj diff --git
   jj log -n 5
   ```

2. Analyze the changes and compose a commit message:
   - Summarize the nature of the changes (new feature, bug fix, refactor, etc.)
   - Write a concise message focusing on the "why" rather than the "what"
   - Use conventional commit format if the project uses it
   - If the user provided a message in the arguments, use that instead

3. Commit with the message:
   ```bash
   jj commit -m "<message>"
   ```

4. Show the result:
   ```bash
   jj log -n 3
   ```

5. Report what was committed and the resulting log.
