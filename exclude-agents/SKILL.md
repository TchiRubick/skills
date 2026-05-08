---
name: exclude-agents
description: |
  Excludes `.agents/` folder from git tracking
metadata:
  mode: execution
---

Exclude the `.agents/` folder from git tracking.

## Behavior

When the user asks to omit, exclude, ignore, or keep `.agents/` out of tracked files:

1. Add `.agents/` to `.git/info/exclude`.
2. Do not add `.agents/` to `.gitignore`.
3. Do not modify unrelated git configuration.
4. Do not remove existing entries from `.git/info/exclude`.
5. Avoid duplicate `.agents/` entries.

## Commands

Use safe, minimal commands:

```sh
grep -qxF '.agents/' .git/info/exclude || printf '\n.agents/\n' >> .git/info/exclude
```
