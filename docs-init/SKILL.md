---
name: docs-init
description: Initialize or refresh a configurable documentation workspace and root `AGENTS.md` using repository inspection.
metadata:
  mode: execution
  approval_policy: on-request
  model_hint: precise-and-pragmatic
---

# docs-init - Documentation Workspace Setup

You are a senior engineer initializing a lightweight docs workspace for this repository.

Create or refresh a root `AGENTS.md` and a docs workspace folder chosen by the user.

---

## Workspace Folder Rule

- Do not assume `.codex/`.
- Determine the workspace folder name from user instruction (examples: `.docs/`, `.ai/`, `.codex/`).
- If no folder name is provided, use `.docs/` and state this explicitly in output.

---

## Safety Rules

- Do not delete files or directories.
- Do not perform destructive rewrites.
- If a file already exists, update it by section merge/append and preserve user-authored content.
- If safe merge is ambiguous, stop and report the exact conflict.

---

## Execution Steps

### 1) Create workspace structure

Ensure this structure exists under the chosen workspace folder `<workspace>/`:

    <workspace>/
      README.md
      constitution.md
      rules/
        core.md
        code-style.md
        safety.md
      context/
        architecture.md
        commands.md
        glossary.md
      tooling/
      snippets/

Ensure root `AGENTS.md` exists.

### 2) Inspect repository

Collect evidence from the repo before writing content:

- `README*` and docs
- Build/test manifests (`package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `composer.json`, `Makefile`, etc.)
- Source directories (`src/`, `app/`, `services/`, etc.)
- CI config (`.github/`, pipelines)
- Existing AI instruction sources (`.cursor/`, `.gemini/`, `.claude/`, `.agents/`, `.opencode/`, `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`)

Use only observed evidence. If unknown, write `Not detected`.

### 3) Populate files (simple format)

Use short, actionable content:

- `<workspace>/README.md`: what the workspace contains
- `<workspace>/constitution.md`: default engineering principles
- `<workspace>/rules/*.md`: concise hard rules
- `<workspace>/context/architecture.md`: module map from observed structure
- `<workspace>/context/commands.md`: real commands discovered from manifests
- `<workspace>/context/glossary.md`: project terms if clearly detected
- `AGENTS.md`: precedence, references to `<workspace>/`, key constraints, and detected other AI instruction sources

Keep content practical and brief. Avoid long templates.

### 4) Merge behavior

When updating existing files:

- Keep existing sections in place.
- Append missing sections.
- Update stale sections with new evidence.
- Do not remove or reorder user content.

---

## Output Requirements

Return a concise report with:

- Workspace folder used
- Created files
- Updated files
- Project structure summary used
- Commands discovered
- Detected other AI instruction sources
- Skipped/unknown items

No filler text.

---

## Completion Condition

Task is complete only when all are true:

- Root `AGENTS.md` exists
- Workspace folder exists with required subfolders/files
- Content is prefilled from repository evidence
- Existing content was merged safely
- Final report includes structure, commands, and detected instruction sources

---
