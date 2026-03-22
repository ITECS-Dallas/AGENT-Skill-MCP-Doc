# Repository Guidelines

## Project Purpose & Structure
This repository is a documentation-first bootstrap reference for Codex CLI setup standards.

Primary content areas:
- `00-overview/` - instruction-layering guidance
- `10-agents/` - repo-local `AGENTS.md` guidance and global-vs-project split
- `20-skills/` - skill authoring guidance
- `30-mcp/` - MCP setup and onboarding guidance
- `40-instructions/` - bootstrap overview and Serena integration patterns
- `50-workflows/` - safety and portability rules
- `60-templates/` - reusable templates for config, `AGENTS.md`, and `SKILL.md`
- `99-inventory/` - provenance and maintenance inventory

Top-level files:
- `README.md` - public GitHub landing page and primary repo overview
- `LICENSE` - repository license
- `.env.example` - safe placeholder file for optional local secrets

## Build, Test, and Development Commands
This repo does not have an application build pipeline. The main work is reviewing and maintaining markdown documents.

Useful commands:
- `git status --short` - inspect the working tree before and after edits
- `find . -maxdepth 2 -type f | sort` - inspect repo contents
- `rg "pattern"` - search for terms, paths, or conventions across the docs
- `sed -n '1,120p' <file>` - inspect a doc section quickly

Validation is primarily editorial:
- check that headings, paths, and examples are internally consistent
- confirm `.env` stays untracked and `.env.example` stays safe to commit
- if you change repo scope or evidence basis, update `99-inventory/source-inventory.md`

## Documentation Style & Naming Conventions
- Use Markdown for all primary content.
- Prefer clear section headings and short, skimmable subsections.
- Use lowercase kebab-case file names.
- Keep the numbered folder taxonomy intact unless there is a strong structural reason to change it.
- Preserve portability: use placeholders like `<PROJECT_ROOT>` instead of live machine-specific values.
- Preserve sanitization: do not add secrets, tokens, auth headers, or client-specific confidential details.
- Prefer patterns and templates over brittle environment-specific runbooks.
- Do not reintroduce snapshot docs that only describe one audited machine or one temporary model catalog.

## Assistant Tooling Requirements
- Serena is helpful for repo navigation and memory, but it is not mandatory for routine markdown edits in this docs-only repo.
- Context7 should be used when changing vendor/library-specific guidance that depends on current official documentation.
- Playwright is not normally required for this repository, since the repo does not ship a web app.
- Avoid destructive git commands unless explicitly requested.
- Before making structural documentation changes, review related files so README, templates, and inventory stay aligned.

## Testing Guidelines
Before finalizing changes:
- re-read the edited markdown for clarity and consistency
- verify file references and folder names are correct
- keep cross-document guidance aligned (for example MCP docs, templates, and README)
- update provenance/inventory docs when adding new source-derived material

## Commit & Pull Request Guidelines
- Prefer commit prefixes like `docs:` for documentation-only changes.
- Group related documentation updates together.
- In commit or PR summaries, mention the major sections changed.
- If a change affects repo rules or source-of-truth expectations, note follow-on files updated to keep alignment.

## Environment & Configuration
- Store secrets only in local ignored files such as `.env`.
- Never commit `.env`; commit only `.env.example`.
- `.serena/` is local tool state and should remain ignored.
- If new local tooling creates stateful folders or files, add them to `.gitignore` unless they are intentional source artifacts.

## Maintenance Rules
- Keep `README.md` accurate as the public landing page.
- Keep `60-templates/` aligned with the guidance in `10-agents/`, `20-skills/`, and `30-mcp/`.
- Keep `99-inventory/source-inventory.md` updated when adding new derived or transformed docs.
- Do not turn this repo into a dump of raw environment state; rewrite, sanitize, or template instead.
- Treat this repo as a bootstrap reference, not as a mirror of one installation.

## Skills
This repository currently does not define repo-local executable skills. It documents skill design and usage patterns instead.
