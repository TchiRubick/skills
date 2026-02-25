# Codex Skills Repository

A curated set of reusable Codex skills for planning, implementation, review, testing, investigation, and workflow orchestration.

Each skill is stored as a standalone Markdown spec and can be invoked by name when working in Codex-enabled environments.

## Repository Layout

- `docs-aftercare/` - post-work insight capture into configurable workspace docs
- `docs-init/` - initialize or refresh a configurable docs workspace + root AGENTS
- `dev-build/` - production implementation mode
- `dev-commit/` - Angular-style commit message generation
- `dev-flow/` - end-to-end team workflow orchestration
- `dev-hotfix/` - emergency minimal-risk patching
- `dev-investigate/` - deep read-only technical investigation
- `dev-locate/` - locate impacted files and dependency paths
- `dev-plan/` - planning-only implementation plans
- `dev-pr/` - PR description generation
- `dev-review/` - senior production code review
- `dev-test/` - focused test authoring
- `init-nextjs/` - initialize/refresh Next.js root AGENTS rules from repo inspection
- `init-python/` - initialize/refresh Python root AGENTS rules from repo inspection
- `init-symfony-laravel/` - initialize/refresh Symfony/Laravel root AGENTS rules from repo inspection

Every folder contains a `SKILL.md` file as the source of truth.

## Quick Start

1. Pick the skill that matches your task.
2. Open its `SKILL.md` and follow the workflow exactly.
3. Keep outputs teammate-facing, concise, and evidence-based.

Useful checks:

```bash
rg --files
rg -n "^name:|^description:" -g "*/SKILL.md"
```

## Contribution Guidelines

- Keep changes minimal and scoped to one skill unless a cross-skill update is required.
- Preserve existing frontmatter and section structure.
- Use direct, operational language and avoid generic guidance.
- Validate examples and command snippets before committing.

Commit style follows Angular-style prefixes (for example `feat:`, `fix:`, `chore:`).

## License

No license file is currently present in this repository. Add one if distribution terms are needed.
