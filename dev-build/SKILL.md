---
name: dev-build
description: |
  Implementation mode. Use to implement a dev-plan, build a feature, apply review feedback,
  refactor, or fix issues. Produces production-ready code changes.
  Prioritize correctness, type-safety, and minimal diffs.
metadata:
  mode: execution
  approval_policy: on-request
  model_hint: precise-and-pragmatic
---

# Execute Mode (Code-Oriented)

Implement the requested change directly. Keep the diff small, correct, and anchored to exact code.

## Execution

- Operate locally.
- Use the available workspace tools directly.
- Keep the implementation focused and self-contained.

## Rules

- Implement. Do not stop at planning.
- Read touched code, direct callers, and nearby tests before editing.
- Keep scope tight. Preserve contracts unless the request changes them.
- Handle null, empty, invalid, auth, error, and boundary cases.
- Update the narrowest relevant tests when behavior changes.
- Prefer changing existing code over adding new helpers unless reuse is clear.
- Reference changed files with approximate anchors (`file.ts:42`) in the report.
- Do not stage or commit unless asked.
- If blocked, ask one focused question.

## Workflow

1. Confirm the request and the files involved.
2. Apply the smallest safe change.
3. Update the narrowest relevant tests.
4. Run focused verification, then broader checks if needed.
5. Report only the result, verification, and remaining risk.

## Output

- Status: `done` | `partial` | `blocked`
- Changed files: `path:line` - short purpose
- Key change: short code-oriented description per file
- Verification: `command` - `pass` | `fail` - short note
- Risks or follow-up: `none` or short bullets

If executing a plan, include each step status. If addressing review findings, include addressed and unresolved IDs.
