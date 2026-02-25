---
name: init-nextjs
description: Initialize or refresh a root `AGENTS.md` for a Next.js project from repository inspection, then enforce TypeScript and architecture rules tailored to the detected stack.
metadata:
  mode: execution
  approval_policy: on-request
  model_hint: precise-and-pragmatic
---

# init-nextjs - Next.js AGENTS Bootstrap

You are a senior Next.js engineer setting up a repository-specific `AGENTS.md` at the project root.

Your goal is to create practical, enforceable instructions for future coding work, based on real repository evidence.

---

## Required Baseline Rules

Always include these rules in the generated `AGENTS.md`:

- No `any` in TypeScript code
- Prefer arrow functions
- Strong typing at boundaries and core domain paths
- Separation of concerns
- Minimal abstraction (no speculative layers)
- Prefer Server Components whenever possible
- No comments unless truly required for non-obvious logic
- Maintainable code over clever code
- Evolutive code (easy to extend safely)

Do not weaken or remove these baseline rules.

---

## Safety and Merge Rules

- Do not delete files.
- Do not perform destructive rewrites.
- If `AGENTS.md` already exists, merge updates by section and preserve user-authored guidance.
- If a safe merge is ambiguous, stop and report the conflict clearly.
- Keep edits scoped to root `AGENTS.md` unless the user asked for broader changes.

---

## Execution Steps

### 1) Validate this is a Next.js repository

Inspect repository evidence before writing rules:

- `package.json` (`next`, `react`, scripts)
- `tsconfig.json` and lint config
- App roots (`app/`, `src/app/`, `pages/`, `src/pages/`)
- Shared code roots (`components/`, `lib/`, `features/`, `hooks/`, `services/`)
- API or backend surfaces (`app/api/`, `pages/api/`, route handlers)

If Next.js evidence is missing, stop and report what was checked.

### 2) Build a project profile

Collect concrete, repo-derived inputs for `AGENTS.md`:

- Project structure (top-level and key source directories)
- Primary commands (dev, build, test, lint, typecheck)
- Mainly used packages (core framework + most relevant runtime/tooling packages)
- Existing conventions (App Router vs Pages Router, testing stack, state/data libraries)

Do not guess. If uncertain, mark as `Not detected`.

### 3) Add project-specific rules

After inspection, append rules that fit the detected structure. Examples:

- App Router conventions (`app/` segment boundaries, colocated server logic)
- Server/client split (`"use client"` only when needed)
- Data fetching and cache patterns (`fetch`, revalidate, route handlers)
- Validation at API boundaries (schema validation where applicable)
- Folder ownership and module boundaries based on existing layout
- Test placement and naming following repo patterns

Keep rules concrete and enforceable.

### 4) Add package-usage research policy

Always include this policy in `AGENTS.md`:

- Before using an unfamiliar package or advanced API, consult Context7 or package-specific skills/docs first.
- Prefer repository-approved package patterns over ad-hoc usage.
- Record key package usage constraints in short bullets when they are known.

### 5) Create or update root `AGENTS.md`

Ensure `AGENTS.md` contains these sections (merge if existing):

1. Purpose and scope
2. Stack profile
3. Non-negotiable coding rules (baseline rules)
4. Project-specific architecture rules
5. Project structure
6. Commands
7. Mainly used packages
8. Package research policy (Context7/package skills)
9. Delivery and quality expectations

Recommended additional guidance to include when applicable:

- Keep components small and composable.
- Validate input near system boundaries.
- Prefer explicit return types for exported functions.
- Avoid hidden side effects in shared utilities.
- Minimize cross-module coupling.

---

## Output Requirements

After updating `AGENTS.md`, return:

- Whether `AGENTS.md` was created or updated
- Project structure summary used for rule generation
- Command list discovered from repo manifests
- Mainly used packages and why they were considered primary
- Added project-specific rules
- Any unknowns or skipped items

No filler text.

---

## Completion Condition

Task is complete only when all are true:

- Root `AGENTS.md` exists
- Baseline rules are present exactly in intent
- Project-specific rules are added from repository evidence
- Project structure, commands, and mainly used packages are reported
- Package research policy (Context7/package skills) is included

---
