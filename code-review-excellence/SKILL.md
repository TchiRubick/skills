---
name: code-review-excellence
description: Master effective code review practices to provide constructive feedback, catch bugs early, and foster knowledge sharing while maintaining team morale. Use when reviewing pull requests, establishing review standards, or mentoring developers.
---

# Code Review Excellence

Use this skill to make reviews sharper, clearer, and more useful.

## Execution

- Operate locally.
- Use the available workspace tools directly.
- Keep the review focused and self-contained.

## Use It For

- Reviewing pull requests
- Defining review standards
- Mentoring through review feedback
- Creating review checklists

## Principles

- Prioritize correctness, security, contracts, performance risks, and tests.
- Skip formatting and lint noise that tools should catch.
- Comment on the code, not the person.
- Be specific, actionable, and evidence-based.
- Separate blocking issues from suggestions.

## Review Flow

1. Get context: goal, scope, PR size, CI status.
2. Do a high-level pass for design, scope fit, and test strategy.
3. Do a file pass for logic, edge cases, security, performance, and maintainability.
4. Return a clear decision and short summary.

## Severity Labels

- `blocking` - must fix before merge
- `important` - should fix or discuss
- `nit` - small non-blocking improvement
- `suggestion` - alternative worth considering
- `learning` - explanation only

## Quick Checklists

Security:
- Input validation
- Auth and authorization
- Secret handling
- Injection or XSS risk

Performance:
- N+1 queries
- Unnecessary loops or repeated work
- Blocking work in hot paths
- Missing pagination or caching where expected

Testing:
- Happy path
- Edge cases
- Error cases
- Deterministic assertions

## Feedback Style

- Prefer questions or suggestions over commands when the issue is non-blocking.
- Make blocking feedback direct and specific.
- Avoid vague comments such as "this is wrong".

## Output

Return only the artifact that matches the request:

- Review feedback: findings ordered by severity, each with problem, risk, and requested change
- Review standard: short checklist, severity labels, and team rules
- Mentoring aid: before/after comment examples plus key advice
