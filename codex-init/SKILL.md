---
name: codex-init
description: Initialize a Codex-only .codex workspace (no symlinks). Creates minimal default files only when missing. Never overwrites existing content.
---

# codex-init — Codex-only Workspace (No Symlinks)

## Objective

Initialize a **Codex-only** workspace for this repository:

- Uses **`.codex/`** as the workspace folder
- **No symlinks at all** (no root entrypoints, no dotfolder links)
- Creates a minimal, consistent structure Codex can rely on
- Only creates files/directories **if missing**

---

## Safety Rules (Mandatory)

- NEVER overwrite existing files or directories.
- If a required path exists but is the wrong type (e.g. file where a directory is required) → STOP and report the conflict.
- Do not delete anything.
- Do not modify existing file contents unless explicitly instructed.
- After completion: print `ls -la` and a tree of `.codex` (depth 4).
- Provide a short execution summary (created/skipped/conflicts). No extra commentary.

---

## Execution Steps

### 1️⃣ Create `.codex/` workspace

Create directory `.codex/` if missing.

Inside it, create this structure:

    .codex/
      README.md
      constitution.md
      entrypoints/
        AGENTS.md
      rules/
        core.md
        code-style.md
        safety.md
      context/
        architecture.md
        commands.md
        decisions.md
        glossary.md
      tooling/
      snippets/

If any of these paths already exist, keep them unchanged.

---

### 2️⃣ Populate minimal default content (only if files are missing)

Create these files only if they do not exist.

#### `.codex/README.md`

    # .codex workspace

    This folder is the Codex workspace for this repository.
    All Codex entrypoints, rules, and shared context live here.

    - Entrypoints: ./entrypoints
    - Rules: ./rules
    - Project context: ./context
    - Tooling notes: ./tooling
    - Reusable snippets: ./snippets

---

#### `.codex/constitution.md`

    # Codex Constitution

    This document defines the default behavior for Codex in this repository.

    ## Core principles
    - Correctness over speed
    - Explicit assumptions (no guessing)
    - Minimal, reviewable diffs
    - Deterministic behavior
    - No hidden side effects
    - Protect production and data

    ## Default mode
    1. Restate the objective
    2. Identify constraints and risks
    3. Propose a structured plan
    4. Define verification steps
    5. Wait for confirmation before implementation (unless explicitly told to implement)

    ## Implementation standards
    - Strong typing and clear APIs
    - Small cohesive modules
    - No dead code
    - No silent fallbacks
    - Avoid unnecessary refactors

    ## Verification discipline
    - Run tests / typecheck / lint / build if available
    - If execution is not possible, state what should be run

    ## Anti-vibecoding policy
    - Do not invent missing requirements
    - Ask when ambiguous
    - Challenge weak architecture
    - Prefer boring, robust solutions

---

#### `.codex/entrypoints/AGENTS.md`

    # Codex Entrypoint

    Primary authority:
    - See ../constitution.md
    - See ../rules/core.md

    Tool-specific notes (Codex) may be added below.
    Do not duplicate global rules here.

---

#### `.codex/rules/core.md`

    # Core Rules (Codex)

    - Default to structured reasoning before implementation.
    - Keep diffs minimal and reviewable.
    - Be explicit about assumptions.
    - Do not touch secrets.
    - Avoid destructive operations without confirmation.

---

#### `.codex/rules/code-style.md`

    # Code Style

    - Prefer clarity over cleverness.
    - Use precise naming.
    - Maintain strong typing.
    - Keep functions small and deterministic.

---

#### `.codex/rules/safety.md`

    # Safety

    - Never commit secrets.
    - Be cautious with database migrations and destructive commands.
    - Propose rollback strategy when modifying production-impacting code.

---

#### `.codex/context/architecture.md`

    # Architecture

    High-level system description, modules, boundaries, and data flow.

---

#### `.codex/context/commands.md`

    # Commands

    - How to run dev
    - How to test
    - How to build
    - CI notes

---

#### `.codex/context/decisions.md`

    # Decisions

    Record architectural decisions:
    - Date
    - Context
    - Decision
    - Consequences

---

#### `.codex/context/glossary.md`

    # Glossary

    Domain terminology and definitions.

---

### 3️⃣ Final Output

Print:

- `ls -la`
- Tree of `.codex` up to depth 4

Then summarize:

- Created files
- Skipped items
- Conflicts (if any)

No additional commentary.
