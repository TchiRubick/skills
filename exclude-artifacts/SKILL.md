---
name: exclude-artifacts
description: |
  Creates `.artifacts/` folder and excludes it from git tracking
metadata:
  mode: execution
---

Create the `.artifacts/` folder and exclude it from git tracking.

## Behavior

When the user asks to omit, exclude, ignore, or keep `.artifacts/` out of tracked files:

1. Create the `.artifacts/` folder if it does not exist.
2. Add `.artifacts/` to `.git/info/exclude`.
3. Do not add `.artifacts/` to `.gitignore`.
4. Do not modify unrelated git configuration.
5. Do not remove existing entries from `.git/info/exclude`.
6. Avoid duplicate `.artifacts/` entries.

## Commands

Use safe, minimal commands:

```sh
mkdir -p .artifacts
grep -qxF '.artifacts/' .git/info/exclude || printf '\n.artifacts/\n' >> .git/info/exclude
```
