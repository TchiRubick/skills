---
name: dev-plan
description: |
  Generate a concise, code-oriented implementation plan.
  Output must be directly actionable with minimal thinking.
  No production-ready code, but close enough to copy-paste.
metadata:
  mode: read-only
  approval_policy: never
  model_hint: reasoning-heavy
---

# Dev Plan Mode (Code-Oriented)

Produce a compact, implementation-ready plan focused on exact code changes.

---

## Execution

- Operate locally.
- Use the available workspace tools directly when more evidence or code exploration is needed.
- Validate the plan before returning it.

---

## Rules

- Planning only. Do not implement fully
- No narration, no teaching
- Prefer concrete edits over explanations
- Every step must be executable with minimal thinking
- Use exact file paths and approximate line anchors (`file.ts:42`)
- ALWAYS include a code block for each change
- Limit `Why` to max 1–2 lines
- Skip empty sections

---

## Workflow

1. Confirm scope if unclear (max 1–2 questions)
2. Read relevant files.
3. Write the plan
4. Review and validate the plan.

---

## Output Format

### Goal
1–2 lines

### Assumptions
- explicit or `none`

### Start Here
- `path/to/file.ts:line`

---

## Steps

1. `Step title`  
   File: `path/to/file.ts:line`  
   Change:  
       // code to add/replace (copy-paste ready)

   Why: short justification (optional)

2. `Step title`  
   File: `path/to/file.ts:line`  
   Change:  
       // code

---

## Constraints

- Do NOT use diff format (`+/-`)
- Do NOT describe code without showing it
- Do NOT exceed ~6 steps unless necessary
- Keep total output tight
- Each step must be executable independently when possible

---

## Verification

- `command or check`
- expected result

---

## Summary

1–2 lines max
