---
name: docs-aftercare
description: Capture durable post-work learnings into a configurable docs workspace for future tasks.
metadata:
  mode: execution
  approval_policy: always
  model_hint: precise-and-pragmatic
---

# docs-aftercare - Post-Work Knowledge Capture

Capture only high-signal learnings from completed work and merge them into the workspace docs.

---

## Workspace Folder Rule

- Do not assume a fixed folder name.
- Use the workspace folder provided by the user.
- If not provided, use `.docs/` and state this in output.
- If the workspace is missing, instruct to run `docs-init` first and stop.

---

## Safety Rules

- Do not delete content.
- Merge into existing sections instead of duplicating.
- If two entries conflict, keep one consolidated and correct version.
- Do not invent learnings.
- Skip trivial or short-lived notes.

---

## Execution Steps

### 1) Review completed work

Extract durable insights from:

- code changes and architecture decisions
- bugs/failures and their fixes
- edge cases and constraints discovered
- reusable patterns/snippets

### 2) Keep only high-signal items

Keep an insight only if it is reusable, non-obvious, or risk-reducing.

### 3) Classify and merge

Write insights into:

- `<workspace>/context/architecture.md`
- `<workspace>/context/commands.md`
- `<workspace>/context/glossary.md`
- `<workspace>/rules/core.md`
- `<workspace>/rules/code-style.md`
- `<workspace>/rules/safety.md`
- `<workspace>/snippets/`
- `<workspace>/tooling/`

If no category fits, create one focused file under `<workspace>/`.

### 4) Output summary

Return:

- workspace folder used
- files updated/created
- one-line description per change
- skipped duplicates or unknowns

No filler text.

---

## Completion Condition

Task is complete only when all are true:

- updates are merged into existing docs safely
- no duplicate/conflicting entries remain
- summary lists all changed files

---
