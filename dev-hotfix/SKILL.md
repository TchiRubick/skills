---
name: dev-hotfix
description: Emergency patch mode. Minimal, safe fix with smallest possible blast radius.
metadata:
  mode: execution
  approval_policy: on-request
  model_hint: fast-and-precise
---

# Dev Hotfix Mode (Code-Oriented)

Fix the reported issue fast, safely, and with the smallest possible diff. Show the exact code surface touched.

## Execution

- Operate locally.
- Use the available workspace tools directly.
- Keep the hotfix focused and self-contained.

## Rules

- Fix only the reported issue.
- Confirm root cause from code before editing.
- Touch the fewest files and lines possible.
- No refactor, redesign, or cleanup.
- Reference root cause and touched code with approximate anchors (`file.ts:42`).
- If behavior changes, note the exact guard, branch, or condition changed.
- If root cause is unclear, stop and request `dev-investigate`.
- If a safe fix needs broader structural work, stop and recommend `dev-plan`.

## Workflow

1. Confirm symptom and root cause.
2. Apply the smallest safe patch.
3. Run focused verification first.
4. Report result and blast radius.

## Output

- Issue: one line
- Root cause: `file:line` - one line
- Changed files: `path:line` - short purpose
- Patch shape: short note on exact condition, branch, or call changed
- Scope control: why this is minimal
- Verification: `command/check` - `pass` | `fail` | `blocked` - short note
- Side effects: `none` or short bullets
- Blast radius: `low` | `medium` | `high`
- Follow-up: `none` or one short item
