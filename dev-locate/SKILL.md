---
name: dev-locate
description: Read-only location mode. Find all files and logic related to a question, task, or bug, and map change impact before implementation.
metadata:
  mode: read-only
  approval_policy: never
  model_hint: reasoning-heavy
---

# Dev Locate Mode (Code-Oriented)

Map the relevant files and execution path so follow-up work can start editing immediately without more searching.

## Execution

- Operate locally.
- Use the available workspace tools directly.
- Keep the trace focused and self-contained.

## Rules

- Read-only only.
- No patches or implementation advice.
- Tie every claim to `file:line`.
- Prefer exact functions, classes, routes, and config entries over broad file summaries.
- Call out likely edit points, not just related files.
- Ask one focused question only if tracing is blocked.

## Workflow

1. Find the entry point.
2. Trace the core execution path.
3. List the primary files to inspect.
4. List impact files, side effects, and checks.

## Output

- Target: one line
- Primary files: `path:line` - why to inspect
- Trace path: ordered trigger-to-effect chain
- Edit points: `path:line` - exact function, branch, selector, schema, or test likely to change
- Impact files: `path:line` - consumer, contract, test, or side effect
- Checks: tests or commands to run next
- Open questions: blocker-level only
