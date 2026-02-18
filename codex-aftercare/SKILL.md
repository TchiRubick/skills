---
name: codex-aftercare
description: Inspect completed work and extract lasting insights into `.codex` for future improvement.
---

# codex-aftercare — Post-Work Knowledge Capture

## Objective

After a task, workflow, bugfix, refactor, or feature implementation is completed, analyze what happened and determine whether any information should be added to `.codex` for future use.

The goal is to evolve `.codex` into a structured, high-signal knowledge base that improves future Codex performance and reduces repeated mistakes.

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
- After completion: print `git status` and `git diff`.

No extra commentary beyond the summary.

---

## Execution Steps

### 1️⃣ Review the Completed Work

Analyze:

- Code changes
- Commit message
- Diff
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

---

### 2️⃣ Classify the Knowledge

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

---

### 3️⃣ Structured Append Format

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
Commit hash / file path / PR link.

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

### 4️⃣ Deduplication Check

Before writing:

- Search `.codex` for similar content.
- If similar content exists:
  - Merge insight into existing section.
  - Add date + source.
- Avoid re-explaining principles already in constitution.

High signal only.

---

### 5️⃣ Validate Signal Quality

Before appending, ask:

- Will this matter in 3 months?
- Would future me forget this?
- Did this cause friction, risk, or deep reasoning?
- Is this reusable?

If the answer is no → skip it.

---

### 6️⃣ Output Summary

After modifications, print:

git status
git diff

Then summarize:

- Files appended
- New documents created
- Skipped duplicates
- Conflicts detected (if any)

No additional commentary.

---

## What This Skill Prevents

- Re-solving the same architectural mistake twice
- Re-discovering the same edge case
- Forgetting implicit constraints
- Losing reasoning context
- Vibecoding drift over time

---

## Intended Usage

Run this skill:

- After completing a feature
- After merging a PR
- After fixing a production bug
- After resolving a complex design decision
- After refactoring core modules
- After debugging a tricky issue

Do NOT run after trivial edits.

---

## Result

`.codex` becomes a continuously improving engineering memory system.

Future tasks become:

- Faster
- Safer
- More consistent
- Less repetitive

Codex learns from your real work — not assumptions.
