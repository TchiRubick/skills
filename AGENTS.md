# Repository Guidelines

## Project Structure & Module Organization
This repository is a skills library. Each skill lives in its own folder and is defined by one `SKILL.md` file.

- Skill folders: `docs-aftercare/`, `docs-init/`, `dev-build/`, `dev-commit/`, `dev-flow/`, `dev-hotfix/`, `dev-investigate/`, `dev-locate/`, `dev-plan/`, `dev-pr/`, `dev-review/`, `dev-test/`, `init-nextjs/`, `init-python/`, `init-symfony-laravel/`
- Artifact pattern: `<skill-name>/SKILL.md`

Keep each skill scoped to one responsibility, and preserve the existing frontmatter + heading structure used across current files.

## Build, Test, and Development Commands
There is no compiled build pipeline here; contributions are Markdown-first.

- `rg --files` lists all tracked files.
- `rg -n "^name:|^description:" -g "*/SKILL.md"` verifies required frontmatter keys.
- `git log --oneline -n 10` checks recent conventions before committing.

If `markdownlint` is installed locally, run it on changed `SKILL.md` files before opening a PR.

## Coding Style & Naming Conventions
Write concise, operational Markdown aimed at implementation teams.

- Folder naming: kebab-case skill names (example: `dev-build`).
- File naming: always `SKILL.md`.
- Frontmatter keys: lowercase (`name`, `description`, `metadata`).
- Section style: short headings, imperative guidance, explicit constraints.

Follow the existing tone: direct, specific, and non-generic.

## Testing Guidelines
Validation is content and workflow consistency.

- Confirm frontmatter is present and valid.
- Confirm command examples are executable in context.
- Confirm output rules do not conflict with constraints.
- For workflow changes, manually trace one end-to-end path described in the skill.

Example check: `rg -n "^## |^### " dev-build/SKILL.md`

## Commit & Pull Request Guidelines
History shows Angular-style prefixes such as `feat:`, `fix:`, and `chore:`.

- Keep each commit focused on one skill or one coherent cross-skill update.
- PRs should include purpose, changed directories, risk/impact, and validation notes.
- Link related issues/tasks when available.
- Include before/after snippets for substantial workflow or wording changes.
