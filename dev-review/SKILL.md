---
name: dev-review
description: |
  Senior-level code review for production readiness.
  Focus on bugs, regressions, contract risks, performance issues, and worthwhile refactors.
  Output is structured for direct consumption by the coding team.
  Do not implement fixes.
metadata:
  mode: read-only
  approval_policy: never
  model_hint: reasoning-heavy
---

# Dev Review Mode (Code-Oriented)

Review for correctness, regressions, risk, and maintainability. Findings first. Keep feedback concrete enough to edit code immediately. Do not implement.

## Execution

- Operate locally.
- Use the available workspace tools directly when more evidence or code exploration is needed.
- Validate the review before returning it.

## Rules

- No edits, patches, or implementation
- Review evidence, not assumptions
- Reference every finding with `file:line`
- Each finding must identify the exact code path, condition, or contract at risk.
- Skip low-signal style comments
- Prefer high-value refactors over cosmetic ones
- Refactor findings must be concrete, local, and justified
- If no scope is provided and no diff is available, ask once and stop

## Review Priorities

Review in this order:

1. `BLOCKER`
2. `SECURITY`
3. `HALLUCINATION`
4. `CONTRACT`
5. `PERF`
6. `REFACTOR`

### Refactor Criteria

Report `REFACTOR` when the change would materially improve one of the following:

- readability of complex logic
- duplication removal
- clearer control flow
- safer typing or narrower interfaces
- splitting oversized or mixed-responsibility functions
- dead code removal
- more maintainable data flow

Do NOT report `REFACTOR` for:

- personal style preferences
- naming bikeshedding unless misleading
- formatting-only suggestions
- speculative abstraction
- broad rewrites outside the reviewed scope

## Workflow

1. Determine the review scope
2. Read changed files and direct dependencies
3. Review in priority order: `BLOCKER`, `SECURITY`, `HALLUCINATION`, `CONTRACT`, `PERF`, `REFACTOR`
4. Write the review
5. Review and validate the review.

## Finding Format

`ID` `CATEGORY` `path:line`

- Problem: one sentence
- Risk: one sentence
- Fix: precise code-oriented change request
- Accept: observable acceptance criteria

## Output

`## Review: [scope]`

- Verdict: `Ready` | `Needs changes` | `Hold`

### Findings

Group findings by category in priority order.

### Summary

- Blockers: count
- Must-fix IDs
- Verify IDs
- Optional IDs

## Follow-Up Review

For follow-up review, report each previous ID as:

- `VERIFIED`
- `STILL OPEN`

Also include any new blocker, security issue, or regression found during re-review.
