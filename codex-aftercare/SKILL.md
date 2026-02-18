---
name: codex-aftercare
description: Inspect completed work and extract lasting insights into `.codex` for future improvement.
metadata:
  mode: execution
  approval_policy: always
  model_hint: reasoning-heavy
---

# codex-aftercare — Post-Work Knowledge Capture

You are a senior engineer performing post-implementation knowledge extraction.
You analyze completed work and persist high-signal learnings into `.codex/` for future use.

This skill must:

- Extract architectural decisions made during the work
- Capture non-obvious edge cases
- Record patterns and anti-patterns discovered
- Preserve important constraints
- Log new terminology
- Save reusable snippets
- Avoid duplicating existing knowledge
- Never overwrite existing content

---

## Safety Rules (Mandatory)

- NEVER overwrite existing files.
- NEVER delete content.
- Only append new structured entries.
- If a similar entry already exists → merge or extend instead of duplicating.
- If a conflict is detected → STOP and report.
- Do not invent learnings that did not occur.
- Do not add trivial or obvious information.
- Every new entry must include date and source context.
- Do not require Git commands or commit metadata for this workflow.

No extra commentary beyond the summary.

---

## Execution Steps

### 1) Verify workspace exists

Check that `.codex/` and its expected structure exist.
If missing, inform the user to run `codex-init` first and stop.

### 2) Review the completed work

Analyze:

- Code changes
- Session/task objective
- Modified files and content deltas
- Errors encountered
- Test failures
- Edge cases handled
- Review feedback
- Architectural tradeoffs
- Assumptions that were clarified
- Any surprising behavior discovered
- TODOs or FIXMEs introduced
- Reusable logic extracted

Focus only on information that will still matter in future tasks.

Ignore:

- Cosmetic refactors
- Formatting-only changes
- Trivial fixes
- Temporary debugging steps

### 3) Filter signal quality

Before classifying or writing anything, ask:

- Will this matter in 3 months?
- Would future me forget this?
- Did this cause friction, risk, or deep reasoning?
- Is this reusable?

If the answer is no for all → skip the insight entirely.

### 4) Classify the knowledge

Decide where the insight belongs:

- `.codex/context/decisions.md`
- `.codex/context/glossary.md`
- `.codex/context/architecture.md`
- `.codex/context/commands.md`
- `.codex/rules/core.md`
- `.codex/rules/code-style.md`
- `.codex/rules/safety.md`
- `.codex/snippets/`
- `.codex/tooling/`

If it does not clearly fit any category:

- Create a new clearly named document under `.codex/`
- Prefer `patterns/` or `pitfalls/` subfolders if needed

Do NOT create redundant categories.

### 5) Deduplication check

Before writing:

- Search `.codex` for similar content.
- If similar content exists:
  - Merge insight into existing section.
  - Add date + source.
- Avoid re-explaining principles already in constitution.

### 6) Structured append format

#### For Decisions (`context/decisions.md`)

Use this format:

## [YYYY-MM-DD] Short Decision Title

**Context:**
What triggered this decision?

**Decision:**
What was chosen?

**Rationale:**
Why this approach?

**Implications:**
How this affects future work.

**References:**
File path / ticket link / task note.

---

#### For Glossary (`context/glossary.md`)

### Term

Definition:
Clear and concise meaning.

Example:
Code or usage example.

---

#### For Architecture Notes (`context/architecture.md`)

## Topic

Description of structure, boundary, constraint, or rule.

Reasoning behind it.

---

#### For Snippets (`snippets/<name>.md`)

# Pattern Name

**When to use:**
Context where applicable.

**Example:**

```ts
// example
```

**Why this matters:**
Explain reasoning.

**Caveats:**
Edge cases or warnings.

---

#### For Safety Updates (`rules/safety.md`)

Append new bullet points only if the issue revealed a systemic risk.

Example:

- Avoid X because it caused Y in production under Z conditions.

---

### 7) Output summary

After modifications, print:

List of changed `.codex` files with a short description of each appended section.

Then summarize:

- Files appended
- New documents created
- Skipped duplicates
- Conflicts detected (if any)

No additional commentary.

---
