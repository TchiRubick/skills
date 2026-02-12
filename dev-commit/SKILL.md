---
name: dev-commit
description: Generate a single Git commit message following Angular commit conventions.
---

## Objective

Generate ONE valid Angular-style commit message based strictly on the final staged state.

## Execution Flow

1. Check for staged changes.
2. If no staged changes exist, output nothing.
3. If a file is partially staged (staged + unstaged modifications):
   - Stage the full file to include all current changes.
4. Ensure the staged area reflects the complete latest state of modified files.
5. Run `git diff --staged` to analyze the final staged changes.
6. Perform a quick surface-level sanity check to detect obvious mistakes:
   - syntax errors
   - accidental debug code
   - broken imports
   - visible runtime risks
7. Do NOT perform deep review, architectural analysis, or speculative improvements.
8. Output ONLY the commit message text.
9. Do NOT execute `git commit`.

---

## Output Constraints (Strict)

- Plain text only
- No markdown
- No code blocks
- No explanations
- No reasoning
- No metadata
- No leading or trailing whitespace
- No emojis
- No trailing punctuation in subject line
- Exactly one blank line between subject and body
- No extra blank lines

---

## Commit Format (Strict)

type(scope): short imperative summary under 50 characters

- concise factual change
- another concise factual change

---

## Content Rules

- Follow Angular commit conventions
- Scope is mandatory
- Use present tense
- Use imperative mood
- Describe WHAT changed, never WHY
- Subject ≤ 50 characters
- Bullets must reflect actual staged changes
- Do not invent changes
- Only include meaningful modifications

---

## Allowed Types

- feat
- fix
- refactor
- perf
- test
- chore
- docs
- ci
- build

---

## Monorepo Rule

If changes are isolated under a specific app directory (e.g., backoffice/, admin/, api/):

app/type(scope): short imperative summary

Example:

backoffice/fix(orders): improve delivery rendering

- adjust table layout
- fix null guard

Apply this prefix only when changes clearly belong to a single app.
