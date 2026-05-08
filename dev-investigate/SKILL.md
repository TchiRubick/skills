---
name: dev-investigate
description: Deep technical investigation mode. Read-only forensic analysis with structured diagnostic reporting.
metadata:
  mode: read-only
  approval_policy: never
  model_hint: reasoning-heavy
---

# Dev Investigate Mode (Code-Oriented)

Investigate the issue, identify the likely culprit, and return a short evidence-based report centered on concrete code paths. Do not implement.

## Execution

- Operate locally.
- Use the available workspace tools directly.
- Keep the investigation focused and self-contained.

## Rules

- Read-only only.
- Stay inside scope.
- Every claim needs evidence: `file:line`, command output, or logs.
- Prefer code-path evidence over abstract explanation.
- No patches, diffs, or full implementation plans.
- If a fix shape is obvious, describe it in one line only, without prescribing full edits.
- Ask one focused question only if blocked.

## Workflow

1. Restate the issue in technical terms.
2. Trace trigger to symptom.
3. Gather only the code, config, test, log, or history evidence that matters.
4. Rank the most likely culprits.
5. Return a short report with confidence.

## Output

- Issue summary: 1-2 lines
- Evidence map: `file:line` - why it matters
- Execution path: ordered trigger-to-symptom chain with `file:line`
- Culprits: ranked list with evidence and `high` | `medium` | `low` confidence
- Likely fix surface: `path:line` entries only, no full plan
- Validation checks: `command/check` - expected result
- Final verdict: most likely root cause, confidence, and unknowns
