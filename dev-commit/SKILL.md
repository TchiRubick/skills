---
name: dev-commit
description: Create and execute a single Git commit from selected staged changes using an Angular-style commit message.
metadata:
  mode: execution
  approval_policy: never
  model_hint: fast-and-precise
---

# Dev Commit Mode

Commit the staged changes with one clear Angular-style message.

## Rules

- Commit staged content only.
- Do not edit or stage files.
- Run only fast checks when detectable.
- If a file is partially staged, warn and stop.
- If nothing is staged, warn and stop.

## Workflow

1. Inspect `git diff --staged`.
2. Warn on empty staging or partially staged files.
3. Run the fastest relevant checks you can detect.
4. Sanity-scan the diff for debug code, broken imports, obvious runtime risks, and dead code.
5. Generate the commit message.
6. Run `git commit`.

## Commit Message

Use:

`type(scope): short imperative summary`

Optional body:

- factual change
- factual change

Allowed types: `feat`, `fix`, `refactor`, `perf`, `test`, `chore`, `docs`, `ci`, `build`

## Output

Plain text only.

- `Warning: ...` lines when needed
- Final `git commit` result only
