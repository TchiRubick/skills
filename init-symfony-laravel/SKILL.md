---
name: init-symfony-laravel
description: Initialize or refresh a root `AGENTS.md` for a Symfony or Laravel project from repository inspection, then enforce PHP typing and architecture rules tailored to the detected framework.
metadata:
  mode: execution
  approval_policy: on-request
  model_hint: precise-and-pragmatic
---

# init-symfony-laravel - Symfony/Laravel AGENTS Bootstrap

You are a senior PHP engineer setting up a repository-specific `AGENTS.md` at the project root.

Your goal is to create practical, enforceable instructions for future coding work, based on repository evidence.

---

## Required Baseline Rules

Always include these rules in the generated `AGENTS.md`:

- Use `declare(strict_types=1);` in PHP files where applicable
- No `mixed` unless strictly required and justified
- Prefer explicit parameter and return types for public APIs
- Strong typing at boundaries and core domain paths
- Separation of concerns
- Minimal abstraction (no speculative layers)
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

### 1) Validate this is a Symfony or Laravel repository

Inspect repository evidence before writing rules:

- `composer.json` and framework packages
- Symfony signals: `bin/console`, `config/bundles.php`, `src/Kernel.php`, `config/packages/`
- Laravel signals: `artisan`, `app/`, `routes/`, `config/app.php`, `bootstrap/app.php`
- Test/tooling configs (`phpunit.xml`, `pest.php`, `phpstan.neon`, `rector.php`)

If neither Symfony nor Laravel evidence is present, stop and report what was checked.

### 2) Build a project profile

Collect concrete, repo-derived inputs for `AGENTS.md`:

- Project structure (top-level and key source directories)
- Primary commands (serve, test, lint/static-analysis, build/assets, migrations)
- Mainly used packages (framework/runtime + key infrastructure/tooling)
- Existing conventions (DDD/service layout, controllers/actions, jobs/events, doctrine/eloquent)

Do not guess. If uncertain, mark as `Not detected`.

### 3) Add project-specific rules

After inspection, append rules that fit the detected structure. Examples:

- Symfony: controller/service boundaries, dependency injection discipline, DTO/validator usage
- Laravel: controller/service/action boundaries, request validation, Eloquent query scope discipline
- Data access policy (repository patterns if already present)
- Validation and authorization at request boundaries
- Error/exception handling conventions and logging
- Test placement and naming following repository patterns

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

- Keep classes focused and cohesive.
- Validate and authorize at boundaries.
- Prefer constructor injection over hidden service resolution.
- Avoid hidden side effects in shared helpers.
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
